---
layout: post
title:      "Third Project - Museum Manager Rails"
date:       2019-09-06 01:48:05 +0000
permalink:  third_project_-_museum_manager_rails
---


For my Rails Project, I decided to make a museum manager as it was one of the first things that came to mind. This was so far the hardest project to do because there were quite many ways I could of went about this. Rails has so many nifty tools that I could play around with. It was quite an interesting learning experience as well.

The two main issues I had with this project were setting up the omniauth for logging in and (surprisingly) the html/css side of it. The front-end side was hard because I couldn't think of how I wanted the site to look until as I played around with it I finally made something that I was satisfied with. 

Setting up the omniauth was problematic because my first attempt to set it up kept getting me 404 errors whenever I tried to login through it. I used some of the videos from the previous labs as my guide when first attempting this. In the sessions controller:

```
      def create
           if auth_hash = request.env["omniauth.auth"]
              @user = User.find_or_create_by_omniauth(auth_hash)
               session[:user_id] = @user.id
               redirect_to user_path(@user)
           else
               redirect_to '/login'
               @user = User.find_by(username: params[:user][:username])
            if @user && @user.authenticate(params[:user][:password])
               session[:user_id] = @user.id
               redirect_to user_path(@user)
            else
              redirect_to '/login'
            end
         end
       end		 
```

And in the user model:

```
  def self.find_or_create_by_omniauth(auth_hash)
    self.where(:email => auth_hash["info"]["email"]).first_or_create do |user|
      user.name = auth_hash["info"]["name"]
      user.password = SecureRandom.hex
    end
  end
```

I searched around for an alternative way to do this and found some answers on Stack Overflow and a few other places where instead of .find_or_create_by the auth_hash, it used provider and uid. Provider being github (or any other site you are interacting with) and unique id.

The new sessions controller's create method: 
```
    if request.env["omniauth.auth"]
      auth = request.env["omniauth.auth"]
      user = User.find_by_provider_and_uid(auth["provider"], auth["uid"]) || User.create_with_omniauth(auth)
      session[:user_id] = user.id
      redirect_to user_path(user.id)
    else
```
It finds by provider and uid from provider or creates the the user with the auth and redirects to the user path.

And the new code in the user model: 

```
  def self.create_with_omniauth(auth)
    create! do |user|
      user.provider = auth["provider"]
      user.username = auth["info"]["name"]
      user.uid = auth["uid"]
      user.email = auth["info"]["email"]
      user.password_digest = SecureRandom.uuid
    end
  end
```

There was also a small issue where I could not access the museums list page when I had no exhibits to display due to a feature that displayed the museum with the most exhibits, and in turn got an undefined method error. I knew the issue but found a few ways to fix with new tools such as .try. Though I choose a more simple solution where I just checked if the exhibits were present with .present?

Overall this project was quite fun, excluding the setting up of the omniauth. 


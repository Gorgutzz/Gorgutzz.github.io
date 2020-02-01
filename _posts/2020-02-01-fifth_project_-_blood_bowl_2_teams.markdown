---
layout: post
title:      "Fifth Project - Blood Bowl 2 Teams"
date:       2020-02-01 23:49:36 +0000
permalink:  fifth_project_-_blood_bowl_2_teams
---


For my React Redux application project, I decided do something related to one of my favorite games, Blood Bowl 2. An app which would allow me to view players and star players of the numerous teams in the game and their stats so that I compare their stats while playing the tabletop or digital versions.  Using postgreSQL for my db, it took me a quite a bit of time to fill in the seed data for all of the teams, their players and star player options as there are more than a hundred for both the former and latter.

I used quite a few actions in this app. These are JS objects that are dispatched to the store whenever the state needs to be updated. It has a type key that describes the action that we are dispatching is something.  There are also ‘Action Creators’ which gives more options and ways to use data in the actions. Here is an example of  an action creator I use:
```
export const fetchPlayers = teamId => {
    return dispatch => {
        dispatch({ type: 'LOADING_PLAYERS' });
        fetch(`/api/teams/${teamId}/players`)
          .then(res => res.json())
          .then(responseJSON => { dispatch({ type: 'ADD_PLAYERS', cards: responseJSON});
            })
    }
};
```

Having Redux in this app was a way for allowing the numerous elements to have access to the same data stored in the store. Any component that was connected to the store has access to the application’s global state. And I used this feature to its fullest extent as I used the mapStateToProps function to map the specific part of the global state I wanted to access to the props for that specific component so it was accessible to use and update through that component’s props. 

Overall this was an interesting project though it did take me quite a while to fully delve into since it is new material. There is still much to leanr but this was a good learning base for future projects with the React framework.


The Traumatic Media DataBase is a project I started in 2021 in order to provide a simple way to search for media which may have a scenes that could be considered traumatic. 

This was inspired through seeing the effects of Birth Trauma on multiple woman I personally know and, through my wife, the effect that the trope of suprise traumatic birth scenes in popular media 
can have.

My plan for this project is to make a robust full stack project and then "give" it to the Birth Trauma Association to aid in raising awareness. This project has also been built with other traumatic events in mind and can be expanding on when needed.

#### GitHub (Currently Private)
[TMDB Project Page](https://github.com/DLBPointon/tmdb_project)

#### Tech Stack
| Technology | Docs | Implimented | Description | 
|--|--|--|--|
| Angular |  |  | Single Page Application |
| PostgreSQL |  |  | The backend database |
| PostgREST |  |  | A database - API layer |

## Issues

### Issue 1 - Schema
Main issue stopping further work is the database schema, there is an issue between the table main_2_traum_ref (which assigns the media to multiple trauma events) and the traumatic_table (which details the type of trauma (which is in no particular order)).

```
db_1   | 2021-09-30 07:31:22.803 UTC [91] ERROR:  insert or update on table "main_2_traum_ref" violates foreign key constraint "traumatic"
db_1   | 2021-09-30 07:31:22.803 UTC [91] DETAIL:  Key (traum_pk)=(1) is not present in table "traumatic_table".
db_1   | 2021-09-30 07:31:22.803 UTC [91] STATEMENT:  COPY main_2_traum_ref FROM '/var/lib/postgresql/tmdb/main_2_traum_ref.tsv' CSV HEADER DELIMITER E'\t' NULL '';
db_1   | psql:/docker-entrypoint-initdb.d/20_db_fill.sql:5: ERROR:  insert or update on table "main_2_traum_ref" violates foreign key constraint "traumatic"
db_1   | DETAIL:  Key (traum_pk)=(1) is not present in table "traumatic_table".
```

Only enough, talking with multiple other people that have worked on databases, the actual code is correct, but something seems to be getting in the way.

#### Fix
I think the database just needs redesigning, it isn't as optimal as it could be.

### Issue 2 - Hosting

I could self-host the application on [[PiStack]], but will there be an issue with scaling as I will be taking this to the Birth Trauma Association, are 4 Pi's enough? 

Security, how would I secure a self-hosted app like this? Is the domain provider able to secure this?

#### Fix
Much more reading, talk to some people who know much more in this topic.

### Issue 3 - Adding new events

I can't sit at a computer verifying new additions, but I also can't have a completely open DB. Security would be a nightmare as, lets face it people would attack it. 

Do I implement a login feature knowing that it would put some people off logging media?

This would require JWS tokens and I just don't know enough in the field.

### Fix 
Much more reading, talk to some people who know much more in this topic.

### Issue 4 - Scoring
We cannot score based on the trauma, it creates a heirarchy of "this trauma is more traumatic than that one". Trauma is trauma and cannot be scored. So I propose a method based on the number of "events" / length of time to consume the media or maybe number of "events" per hour/page. This could be calculated in the DB or on the fly with some JavaScript.

A score based on the number of triggers, length of film/book/show as an indicator of whether you should watch it Maybe something like in grt-realtime, javascript traffic light for if trigger score above x then give traffic light colour.
# Sprint 1 Design Document Template

## Deployment Environment

[Link to your deployment environment]: http://ec2-3-17-10-157.us-east-2.compute.amazonaws.com:3333/

## Functional Requirements

1. Home Page Redesign Use Case
	- Modify the layout of the homepage to display more than 4 projects 
		- List projects with a number of repos statistic 
		- Need to modify the CSS file to allow projects to overflow in the pane 
		- Edit the DownloadedReposCard to display the number of repos in each project 
		- 
2. Use Case Name B		
	- Functional Requirement 1
	- Functional Requirement 2
	- ... etc.
3. ... etc. 

## Database Design

### ERD



### DDL 

% Total repo count.  
select sum(repos_count) from\
(select a.`name`, count(*) as repos_count\
from projects a, repos b\
where a.id = b.projects_id\
group by a.id\
order by a.`name`) a

% Just the projects and number of repos  
select a.`name`, count(*) as repos_count\
from projects a, repos b\
where a.id = b.projects_id\
group by a.id\
order by a.`name`

## Files that are stubbed out in your repository, with comments about the use cases they are connected to. These sections may not all exist for the Zephyr project teams. Simply explain them as best you can. 

### User Interface Files

1. frontend/app/styles/ghdata.style 
2. frontend/app/components/DownloadedReposCard.vue
3. etc.


### Model Files (Database Access)

1. augur/datasources/ghtorrent/ghtorrent.py
2. augur/datasources/ghtorrent/routes.py
3. etc


### Controller Files (API or other)

1. first one 
2. second one
3. etc. 

## Describe languages you need to use, and any gaps in skills on your team. 

1. Javascript 
	- Brian has some experience with JS but none with vue or any JS on the level of this project. Need to use JS to display the number of repos in each project.  
2. MYSQL
	- Needed to pull the data about number of repos and name of the projects. MYSQL needed for the first use case was provided by professor Goggins
3. Skill gaps, if any, otherwise specify who is doing what
    - Brian is not familiar with python, or vue JS. He also has no experience with a project of this scale. 
    - 
    -  

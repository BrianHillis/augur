# Sprint 1 Design Document Template

## Deployment Environment

http://ec2-3-17-10-157.us-east-2.compute.amazonaws.com:3333/

## Functional Requirements

1. Home Page Redesign Use Case
	- Modify the layout of the homepage to display more than 4 projects
		- List projects with a number of repos statistic
		- Need to modify the CSS file to allow projects to overflow in the pane
		- Edit the DownloadedReposCard to display the number of repos in each project

2. Home Page Search Function Use Case		
	- Add a Search function on the homepage so that users can search for the specific projects they want
		- Add Search bar and Search button for the homepage
		- Modify the CSSfile to allow homepage to display the search bar and button
		- Add search function to DownloadedReposCard to return certain projects only contains key words

3. Home Page Sort Function Use case
	-Add a sort bar to the homepage
		-Add a dropdown and "Sort" button to homepage so users can sort repos in Database in a number of different configurations
		-Modify CSS to display dropdown and button
		-Add sort funciton to DownloadedReposCard to order outputted repos by the selected value

## Database Design

### ERD

![ERD](https://github.com/BrianHillis/augur/blob/master/Screen%20Shot%202019-04-14%20at%205.07.19%20PM.png)

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

1. augur/datasources/facade/facade.py
2. augur/datasources/facade/routes.py
3. etc



## Describe languages you need to use, and any gaps in skills on your team.

1. Javascript
	- Brian has some experience with JS but none with vue or any JS on the level of this project. Need to use JS to display the number of repos in each project.  
	- Weiwei has some experience with html and JS but none with vue. Need to add search bar and button,parse the projects array and return certain results using JS.
	-Thomas also has some experience with html and JS, but none with vue. Need to use JS to interpret and act on data from the sort form to reorder all repository items, ideally without reloading the page.
2. MYSQL
	- Needed to pull the data about number of repos and name of the projects. MYSQL needed for the first use case was provided by professor Goggins
3. Skill gaps, if any, otherwise specify who is doing what
    - Brian is not familiar with python, or vue JS. He also has no experience with a project of this scale. In order to implement the Home Page Redesign, Brian will use other vue cards as examples when trying to redesign the home page. Being active in the slack channel and attending the hack space provided by Professor Goggins have also been very useful.  
    - Weiwei is not familiar with vue JS. She will try to learn some vue knowledge online and do some test experiments. Meanwhile she can use some resource provided by classmates and Professor Goggins in class or slack. Weiwei is working to implement a search function for the returned repositories.
    -  Thomas is not familiar with vue.JS or this sort of webapp. He'll learn the necessary vue and brush up on the necessary javascript to complete his task: implementing a sort function for all returned repos.

Design Document




Link to our EC2 instance:
http://ec2-3-17-10-157.us-east-2.compute.amazonaws.com:3333/


Use case 1: Home Page redesign

    System requirements

      - This use case requires accessing the length of the array holding each github repository link. This is done through a for loop that accesses each project in the repos array and getting the number of repositories in the project.

      - This use case also changes the style of the page to allow for overflow to display multiple projects.

    Design Decisions

      - I chose to add the number of repos stat in the head of the table for easy viewing and to eliminate the repition of displaying the stat with each link

      - I chose to allow for overflow of the project cards instead of a list of projects with the number of repos stat that acted as a link to a new page that displayed all the repo links because this allowed for more information to be displayed on the current interface.

    Database Usage

      - This use case did not end up needing to make any changes to the database, only access information that was already retrieved from it.

Use case 2: Sorting the cards on the home page

      System Requirements

        - This use case requires accessing the array of projects and directly manipulating the HTML DOM

        - Additionally, this use case requires sorting and a complete re-arrangement of the home page

      Design Decisions

        - I chose to use a very simple layout with a full-width selector and a left-aligned button for the sake of simplicity and to have the smallest footprint without looking too bad

        - I chose to otherwise keep the re-arranged layout the same after a sort for the sake of consistency

      Database Usage

        - This use case did not require database access, as it relied solely on the arrays made available through Vue.js for sorting

Use case 3:Searching the cards on the home page

System Requirements

    - This use case requires accessing the array of projects and directly manipulating the HTML DOM

    - Additionally, this use case requires searching through all projects and return projects whose name contain key words.At last we need to re-arrange of the home page

Design Decisions

    - I chose to use <input> element to create the search bar.And I wrote a command to get the key word.
`var searchItem = document.getElementById("search").value;` once users key in some words, we can trigger the searching query like this: `searchItem.onclick = getSearchResults;`

    - I am still working on how to get a full array of projects' names from the HTML.After that I am going to finish search function like this:

methods:{
    search(){
        this.projectslist=[];
        for(let i=0;i<this.newlist.length;i++){
            //if not contain key word, then return -1
            if(this.projectlist[i].value.indexOf(this.searchval)>=0){
                this.projectslist.push(this.projectlist[i]);
            }         
        }
        return this.projectslist;    
    },    


Database Usage

    - This use case did not require database access, as it relied solely on the arrays made available through Vue.js for searching.


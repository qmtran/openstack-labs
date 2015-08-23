# Lab 2 - RDO Horizon Interface

  Lab Objectives:

  0. Become familiar with the OpenStack Horizon Interface

## Login to the Horizon Interface

  0. Login to the OpenStack Horizon Web Interface by navigating your browser to the public IP address of your instance, explore the accessible pages and fill in the table of information

    ![Image of login](img/horizon-login.png)
    
    ![Image Dashboard](img/horizon-dashboard.png)


  0. Navigate around the interface, find and document the below values
    :red_circle: TODO find these items from interface

    | Info to find | Value |
    | -------------| ----- |
    | Item 1 | |
    | Item 2 | |
    

## Add a Project:

  0. Navigate to: Identity > Project > +Create Project
     
     ![Create Project](img/create-project.png)
     ![Create Project](img/create-project2.png)
     ![Create Project](img/create-project3.png)

## Add a User:

  0. Navigate to: Identity > Users > +Create User

     ![Create User](img/create-user.png)
     ![Create User](img/create-user2.png)
     ![Create User](img/create-user3.png)

## Member Interface

  0. Logout from the `admin` account and login as `student`
  0. Explore :red_circle: TODO: table of things to find/document

## Add a Private Network

  0. Navigate to: Project > Network > Networks > +Create Network

     ![Create Network](img/create-network.png)
     ![Create Network](img/create-network2.png)
     ![Create Network](img/create-network3.png)
     ![Create Network](img/create-network4.png)

     > :white_check_mark: **Additional Info**:
     >
     > The Allocation Pools is the `start,end` addresses for the pools.
     > The entry form for this field does not parse spaces.
     > Example Pool: `192.168.1.100,192.168.1.120`

     ![Create Network](img/create-network5.png)

## Add a Router

  0. Navigate to: Project > Network > Network Topology > +Create Router
     
     ![Create Router](img/create-router.png)
     ![Create Router](img/create-router2.png)
  
  0. Either click on "View Router Details" or choose our new router from the list on Project > Network > Routers

     ![Create Router](img/create-router3.png)
     ![Create Router](img/create-router4.png)

  0. Add an interface to the new router

     ![Create Router](img/create-router5.png)
     ![Create Router](img/create-router6.png)
     ![Create Router](img/create-router7.png)

  0. Set the Gateway for this network

     ![Create Router](img/create-router8.png)
     ![Create Router](img/create-router9.png)

  0. View the Network Topology and Networks page and verify configurations

     ![Create Router](img/create-router10.png)
     ![Create Router](img/create-router11.png)

#### [Next Lab](../lab-03)    

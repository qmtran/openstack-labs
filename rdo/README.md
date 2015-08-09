# RDO Lab

:red_circle: TODO A well thoughout over-view paragraph about what this lab is about should go here.

Lab Objectives:

## Lab 0 - Document Lab IP addresses
 
Your instructor will provide two IP addresses for this lab. 

         | Controller    | Compute     |
-------- | ------------- | ----------- |
Public   | CONTROLLER IP | COMPUTE IP  |
Internal | A.B.C.D       | A.B.C.D     |

0. Edit this README.md file and add the ip addresses to your forked repository.
  * You can make these changes in the github webpage or from your checkedout version.
  * Make sure your changes are committed and pushed to github.com and then refresh the page.

0. Record your instance's internal IP address in the table
  
   * `ssh centos@<IP> -i student.pem` 
   * `ip addr show dev eth0`

0. Set the hostname on each to help with command line differentiation

   * `sudo hostname <controller or compute>`
   * `bash` to show the result 


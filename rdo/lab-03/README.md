# Lab 3 - RDO Horizon Interface, Part Deux

  Lab Objectives:

  0. Launch an instance from the Horizon interface

## Launch an Instance:

  0. Open the Horizon interface (navigate your browser to the public IP address of the controller)
  0. Login to the Horizon interface as the user created in [Lab 2](../lab-02)
  0. Navigate to: Project > Compute > Instances > Launch Instance
  
    ![Launch Instance](img/horizon-launch.png)

  0. Set details and Launch

    ![Set details](img/horizon-details.png)
    ![Launch](img/horizon-spawn.png)
 
  0. Open console, login and interact with the newly launched instance
    
    :red_circle: TODO: haven't cracked the nut yet on RDO's VNC PROXY
    ![Instance details](img/horizon-active.png)
    ![Console tab](img/horizon-console.png)
    ![Console VNC](img/horizon-console2.png)
    

  0. Use `ssh` to access and interact with the newly launched instance

    * Ensure you are currently ssh'ed into the controller instance
    * If not follow steps from previous lab
    * `ssh cirros@10.0.0.2` (password `cubswin:)`)

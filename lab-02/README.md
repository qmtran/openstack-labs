# Lab 2

## Add a User on Devstack (Horizon Interface)
  
  :red_circle: TODO, currently broken in DevStack

## Add a Project on Devstack (Horizon Interface)

  :red_circle: TODO, currently broken in DevStack

## Launch an Instance on DevStack (Horizon Interface)

  0. Open the Horizon interface (navigate your browser to the public IP address)
  0. Project > Compute > Instances > Launch Instance
  
    ![Launch Instance](img/horizon-launch.png)

  0. Set details and Launch

    ![Set details](img/horizon-details.png)
    ![Launch](img/horizon-spawn.png)
 
  0. Open console and interact with the newly launched instance
    
    ![Instance details](img/horizon-active.png)
    ![Console tab](img/horizon-console.png)

    > :red_circle: **DevStack Issue**:
    >
    > The VNC link provided uses the internal IP address of the controller.  You will need to modify this to be the public IP address.

    ![Console VNC](img/horizon-console2.png)

  0. Use `ssh` to access and interact with the newly launched instance

    * `ip addr show` Ensure you are currently ssh'ed into the controller instancae, if not follow steps from previous lab
    * `ssh cirros@10.0.0.2` (password `cubswin:)`)


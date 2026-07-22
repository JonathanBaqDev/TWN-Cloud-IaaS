# Java-React app deployed on Digital Ocean Example

An example of how to deploy an existing Java-React application on a Digital Ocean Droplet.

## Provision VM
- Create a "Droplet" VM on Digital Ocean
- Generate an SSH key pair using `--ssh-keygen` and add the public key to Digital Ocean
- Create a firewall rule to allow inbound connections from SSH - TCP - 22 from the IP of the device you will use to connect
- SSH to the Droplet
- Once connected, install Java 17 using `apt install`

## Deploy application build
- Clone the repository (original repos cited below)
- On your local machine, build the application using `gradle build`
- The .jar file will be in build/libs - copy to your Droplet using `scp <file path> <root@droplet-public-IP:/root>`
- On the Doplet in the directory of the copied file, run the application using `java -jar <file.jar>` - run in the background by adding `&` to the command
- Back on Digital Ocean, add a firewall rule to allow inbound connections to TCP - 7071
- On a web browser, access the running application using `<Droplet-public-IP>`:7071

## Best Practice: Create VM user
- On the Droplet, create a new user using `adduser <username>`
- Add your new non-root user to the sudo group using `usermod -aG sudo <username>`
- Switch to your new user and create a directory ~/.ssh/authorized_keys
- Copy your public key to the newly created directory
- You can now SSH to the Droplet and safely run the application with a non-root user account

<hr/>
Cloned repo can be found here: https://gitlab.com/twn-devops-bootcamp/latest/05-cloud/java-react-example
Original project can be found here: https://github.com/pmendelski/java-react-example 

# Java-React app deployed on Digital Ocean Example

An example of how to deploy an existing Java-React application on a Digital Ocean Droplet.

## Provision VM
- Create a "Droplet" VM on Digital Ocean
- Add your SSH key - generate using `--ssh-keygen` and add the public key
- Create a firewall rule to allow inbound connections from SSH - TCP - 22 from the IP of the device you will use to connect
- SSH to the Droplet
- Once connected, install Java 17 using `apt install`

## Deploy application build
- Clone the repository (original repos cited below)
- On your local machine, build the application using `gradle build`
- The .jar file will be in build/libs - copy to your Droplet using `scp <file path> <destination path>`
- On the Doplet in the directory of the copied file, run the application using `java -jar <file.jar>` - run in the background by adding `&&` to the command

## Best Practice: Create VM user
-WIP

<hr/>
Cloned repo can be found here: https://gitlab.com/twn-devops-bootcamp/latest/05-cloud/java-react-example
Original project can be found here: https://github.com/pmendelski/java-react-example 

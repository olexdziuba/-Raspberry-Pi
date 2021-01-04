# Install DOCKER on Raspberry pi

### Update systeme
*sudo apt-get update && sudo apt-get upgrade*

### Download docker with curl
*curl -fsSL https://get.docker.com -o get-docker.sh*

### Run the installation script using the command:
*sudo sh get-docker.sh*

### ADD not root user to the Docker Group 
*sudo usermod -aG docker [your_user]*
ex. for user *'pi'* - the default user in Raspbian: *sudo usermod -aG docker pi*

### Check docker version / info
*docker version* 

*docker info*

### Install docker-compose
sudo apt install -y docker-compose

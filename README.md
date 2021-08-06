# Setting up an AWS VPC
## Firstly navigate to the VPC page and click create VPC

![image](https://user-images.githubusercontent.com/76522579/128516904-1d72b3a6-8606-482b-8d0c-6ecfa841406b.png)
  
- In this section create a name for your VPC, this will be used to identify your newly created VPC at a later date.
- In the CIDR space put the IP that you want to use for the private network. In this example we will be using `10.200.0.0/16`
- When completed the VPC should look as such:

![image](https://user-images.githubusercontent.com/76522579/128517896-93db3186-0b00-4e01-9580-792807cc0264.png)

## Creating the subnets

![image](https://user-images.githubusercontent.com/76522579/128518186-1dce32cd-65b1-4a4c-a4ba-ba4f3ff47750.png)

- In this section you need to name the subnet as well as specifiy the CIDR block.
- For this example three subnets will be created:
  - Public - for connecting to the app
    - The IP used for this subnet is 10.200.1.0/24
  - Private - for the app to connect to the database
    - The IP used for this subnet is 10.200.2.0/24
  - Bastion - to connect to the database with ssh
    - The IP used for this subnet is 10.200.3.0/24

## Internet Gateway

- The next step is to create the internet gateway, this will be used to connect the subnets to the Internet.
- Creating a new internet gateway is as simple as navigating to the internet gateway page and creating a tag for it.
- Next will be associating a routing table with the internet gateway.
- After navigating to the routing table and creating a routing table associated with the VPC previously created.
- Add the newly created internet gateway to the route table with the destination as `0.0.0.0/0` which should now look like this:

![image](https://user-images.githubusercontent.com/76522579/128520847-da035189-cc20-4ef4-9e4e-4acb2144de72.png)

- Go into subnet associations and select both the public and bastion subnets

![image](https://user-images.githubusercontent.com/76522579/128520992-b9ee2abc-1f45-4a2c-bcd1-2085b71efafc.png)

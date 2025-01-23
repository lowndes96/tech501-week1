subnet 

virtual network is like an apartment, subnets are like the rooms in the appartment 

public subnet 10.0.2.0/24 + private subnet 10.0.3.0/24 - all use sections of the space (not full half)

tech501 - emily-2-subnet-vnet 
space (CIDR) 10.0.0.1/16 aprox 65,000 IPadresses 

look up IP version 4 

[virtual network vid](https://www.youtube.com/watch?v=u0TgGIn2LIM)

### virtual networking video notes 

underlay 
- physical structures

  * fabric - all physical components needed to run a virtual network
  * TEP - tunneling end point - point where the virtual network 'toutches' the physical network 
  * routing - can be virtual or physical - and bridges (will be in both virtual and physical environment, its an interface!)
  * no inteligence, just connects everything 
  
overlay (the virtual network)
* segments - a layer 2 element on its own 
* transport zone (collection of segments) way to limit which physical devices the virtual network can run across
* routers and bridges - you can have an entierly virtual router 
* micro-segmentation - can insert multiple services such as a firewall 
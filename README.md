# peer-to-peer-network
  The contents is briefly about the Evolution of peer-to-peer network. Resource and in the end are the source for exploring deep into 4 peer-to-peer algorithms in 3rd Generation: https://pdfs.semanticscholar.org/a120/fa11ad00af1da49d0dd093b2067dedb1c435.pdf

-1st Generation:  
First peer-to-peer(P2P) also known as Centralized model which mean that most of peers are equal but some peers have more advanced function to manage request and response in the network call “Server”. Server store the path of the resource that simple peer willing to share and when the server get request Server will give the path directly to the peer the contain resource then that 2 peers (peer request, peer response) they both directly connect and begin the process this time we no need Server anymore. The main Disadvantage to this is when the more peers grow Server will imply scalability limit.

-2nd Generation:  
This generation has Flooded Request Model. Here no more Server exist every peer are equal to each others.
. Peer doesn’t inform others peer about the file to share
. when peers want to locate some file the directly send request directly to the peers that contain the file. If file doesn’t exist it’ll resend to others peers that they connected, usually take 5-9 steps to archieve.  
-> When new peer join the network: In order to join the network new peer need to send information about IP address and port to several know host after that new peer can start to send request.

+. It’s seem to work perfectly when number of peers are small, whenever peers grow Flooded may consume a lot of bandwidth then will reduce scalability of the system. The other problem is call Freeriding which happen when most peers already download some file but they not willing to share those file to other request so peers that store file will again act like Server again because it has small number of peers to share the file.  
+. To avoid this problem one more solution come. It’s that peer that has powerful computer and fast internet connection are assign to be Supernode. Peer that want to share the file they can inform to supernode. So when request happen it is not flooded through all peers but through supernode instead(the higher you participate you will get the priority)

-3rd Generation:  
     Document routing model is most recent model use in pure P2P system. When a peer what to share file, they need to hash the name and contents of the file the attach it with the file as file ID. Then those file will store at the peers that have similiar to the file’s ID. When peer want the file they send request of the peer that has similiar ID as file they want. After that every peers that participate that process will keep the path in order to get that file so when the same request happen again the can provide the path quickly no need to find the peer that contains the file again.  
Document routing seem to be effective with a lot of peers in the network but the problem still reamin:  
. ID’s of request file must be know before sending request which make search hard to implement  
. Peer that want to locate file must be know about information that use for hash when it created  
. Hashing different filename result different hash ID so require file not be found  
. Islanding Problem: when peer split to the group which not connect to each other.  

There 4 algorithms to solve those problem of Document Request Model :  
    1. Chord    
	    ->	https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf  
    2. Tapestry      
		->	http://www.srhea.net/papers/tapestry_jsac.pdf  
    3. Pastry      
	    ->	http://rowstron.azurewebsites.net/PAST/pastry.pdf  
    4. CAN(content addressable network)    
		->	https://people.eecs.berkeley.edu/~sylvia/papers/cans.pdf  

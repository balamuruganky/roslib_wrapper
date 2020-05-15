Here it's the deal!!!
=====================

	* Communicate to ROS Robot through web interface. roslibjs and rosbridge_websockets can be used for this. Though roslibjs documentation covers most part, thin wrapper can help the developers. These javascript plugins covers the most important part of ROS communication such as,

		* ROS Connection
		* ROS Parameter
		* ROS Service
		* ROS Topic

RosConnection:
--------------

	Parameters:
	-----------
        $serverUri         : "localhost", /* ROS server IP or Host name (string). Default to "localhost" */
        $serverPort        : "9090",      /* ROS bridge websocket port number (string). Default to "9090" */
        $isSecured         : false,       /* Whether websocket secure. if secure 'wss:' is created. (boolean). Default to false */
        $reconnectInterval : 10           /* Reconnect interval. If 0 or negative, reconnect is disabled (number). Default to 10ms */

    Methods:
    --------
    	* getRos() 								: Get roslibjs object
    	* isConnected() 						: Check whether connection available or not
    	* getTopicsList() 						: Get the list of topics available in ROS as JSON format string
    	* getNodesList() 						: Get the list of nodes available in ROS as JSON format string
    	* getParamsList() 						: Get the list of parameters available in ROS as JSON format string
    	* getServicesList() 					: Get the list of services available in ROS as JSON format string
    	* registerRosConnectedCallbackFn() 		: Callback function to notify the client when WS connection established.
    	* registerRosDisconnectedCallbackFn() 	: Callback function to notify the client when WS disconnected.

RosTopic
--------

	Parameters:
	-----------
		$rosConn  		: null  /* RosConnection object (object). Default to null */
		$name   		: null  /* ros topic name (string). Default to null */
		$messageType 	: null  /* ros topic message type (string). Default to null */

	Methods:
	--------
		* get$Topic() 				: Get RosTopic object
		* subscribe(callbackFn) 	: Subscribe to topic. method as argument.
		* unsubscribe() 			: Unsubscribe the topic
		* publishMsg(ROSmessageJSON): Publish message to the topic. JSON string as argument.

RosParam
--------

	Parameters:
	-----------
		$rosConn  	: null  /* ros_connection object (object). Default to null */
		$name   	: null  /* ros param name (string). Default to null */

	Methods:
	--------
		* get$Param() 		: Get RosParam object
		* get(callbackFn)	: Get the param value. method as argument.
		* set()				: Set the param value

RosService
-----------

	Parameters:
	-----------
		$rosConn     : null  /* RosConnection object (object). Default to null */
		$name        : null  /* ros service object (string). Default to null */
		$serviceType : null  /* ros service type (string). Default to null */
		$request     : null  /* ros service request (json string). Default to null */
		$response    : null  /* ros respose callback function (method). Default to null */

	Methods:
	--------
		* get$Service 				: Get RosService object
		* call(request, response) 	: Call the service request. 
									  Request should be JSON string. 
									  Response should be a method.

Demo
====

roslib_wrapper javascript plugin functionalities are demostrated with the famous turtle simulator.  

	Setup
	------
		- Start the below 2 nodes in ROS setup
			* roslaunch rosbridge_server rosbridge_websocket.launch (Launch websocket in the host machine with port number as 9090)
			* rosrun turtlesim turtlesim_node  (Run the turtle simulator)
		- Open the demo/ros_connection_demo.html in any browser. But tested in Chrome and Mozila :)

More details, please refer wiki page.
#############
tensorflow
#############

	It is framework to define and run computations involving tensors.


What is a tensor?
	It is a data structure to represent all data (only the tensors are passed in the operations in the computational graph). Tensors are immutable.
	A Tensor has a rank, a shape and a static type so it can be represented as a multidimentional array of numbers.

Tensor properties:

* Data type: float32, int32 or string 
	     A tensor will consist of same data type.

* Shape: The number of dimensions it has and the size of each dimension.

* Rank: Rank is the number of dimensions.

.. note:: Rank is different from what we learnt in matrix.

.. csv-table:: Rank
    :header: "Rank", "Stands for"
    :widths: 10, 30

    0, "Scalar"
    1, "vector"
    2, "matrix"
    3, "3-Tensor"
    4, "n-Tensor"


Variable
==================

	It stores a persistent tensor.

* *tf.Variable* represents tensors.

* modification on a given variable is visible to all sessions.

**Example:**

*my_variable = tf.getvariable("my_variable",[1,2,3])*

.. note:: default data type is float32.
     default initializr is

Variable Collection
*********************

	Every variable gets placed in the following two collections:

1. Global Variable - Variables that can be shared across multiple devices.

2. Trainable Variable - For which Tensorflow will calculate gradients(learning variable).

                                        **OR**
3. Local Variable - If you dont want the data to be trainable use Local variable.
	Syntax: *tf.GraphKeys.LOCAL_VARIABLES*

                                        **OR**

4. Specify in the argument at the starting in variable as *trainable=False*.

Device Placement
********************

	It is used to place variables on a paticular device and to make better utilization of the hardware.  

Initializing Variables
**************************

	Low level initialisation saves computational power.

	Explicit initialization is otherwise useful because it allows you not to rerun potentially expensive initializers when reloading a model from a checkpoint as well as allowing determinism when randomly-initialized variables are shared in a distributed setting.

* To initialize all trainable variables in one go - *tf.global_variables_initializer()*. This function returns a single operation responsible for initializing all variables in the *tf.GraphKeys.GLOBAL_VARIABLES* collection.

* To get the names of all variables which have not yet been initialized:

*print(session.run(tf.report_uninitialized_variables()))*

.. note:: By  default *tf.global_variables_initializer* does not specify the order in which variables are initialized. Therefore, if the initial value of a variable depends on another variable's value, it's likely that you'll get an error. Any time you use the value of a variable in a context in which not all variables are initialized, it is best to use variable.initialized_value() instead of variable.

Using Variables
********************

	To assign a value to variable use assign, assign_add and friends

Graphs and Sessions
======================

Data Flow
***************

	It is a programming model for parallel computing.
+---------+-------------------------------------------------------------+
| Node    | Represent the unit of computation				|
+---------+-------------------------------------------------------------+
| Edges   | Represent the data consumed or produced by a computation	|
+---------+-------------------------------------------------------------+

tf.Graphs
*****************

	Contains two relevent kind of information.

* Graph structure: Used to lay the structre of the graph flow.

* Graph Collection: A general mechanism for storing collections of metadata in a tf.Graph

+------------------------+-----------------------------------------------------------+
| *tf.add_to_collection* | Enables you to associate a list of objects with a key     |
+------------------------+-----------------------------------------------------------+
| *tf.get_collection*	 | Enables you to look up all objects associated with a key  |
+------------------------+-----------------------------------------------------------+

+-----------------+-------------------------------------------------------------------+
| Graph		  | Contains a set of *tf.operation* objects		       	      |
+-----------------+-------------------------------------------------------------------+
| *tf.operation*  | (Node) Represents unit of operation				      |
+-----------------+-------------------------------------------------------------------+
| *tf.Tensor*	  | (Edge) Represents unit of data that flows between operation	      |
+-----------------+-------------------------------------------------------------------+

Building a graph
********************

.. note:: TensorFlow provides a default graph that is an implicit argument to all API functions in the same context as given below.

**Example:**

    Calling tf.constant(42.0) creates a single tf.Operation that produces the value 42.0, adds it to the default graph, and returns a tf.Tensor that represents the value of the constant.

*Similarly* for 1. tf.matmul(x,y)
		2. v=tf.Variable(0)
		3. tf.train.Optimizer.minimize

Executing graph in tf.Session
************************************

* *tf.Session* class to represent a connection between the client program-typically a Python program

.. note:: It caches information about your tf.Graph so that you can efficiently run the same computation multiple times.

**Example**
For low level Tensorflow API
.. code:: # Create a default in-process session. 
	  with tf.Session() as sess:
	  # ...

	  # Create a remote session.
	  with tf.Session("grpc://example.org:2222"):
	  # ...

* *tf.Session.init* accepts three optional arguments:

1. target
2. graph
3. config



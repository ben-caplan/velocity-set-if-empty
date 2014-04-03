Velocity Set If Empty Macro (dotCMS)
=====================

Set a variable value if the variable has not already been set. 

Often when coding in VTL I want to use something like this:

	#if( !$UtilMethods.isSet( $name ) )##
		#set( $name = 'Ben' )##
	#end##

The only problem is that I need to write that 30+ times and that can get kind of ugly... Hence this solution:

	#macro( setIfEmpty $var $value )##
	  #if( !$UtilMethods.isSet($!context.get($var)) )##
	    #set( $_dummy = $context.put($var, $value ) )##
	  #end##
	#end##

To use this include the above code (also found in this repo's VTL file) and then use the following call:

	#setIfEmpty( 'name' 'Ben')##

In this example name will become $name and will have a value of "Ben". Problem solved! 

# kt_sandesha2
Sandesha2/c

#Instruction
First compile kt_axis2c-unofficial then compile sandesha

#Additional note
Require Rampart/c

#Compile MAC OSX 
./configure --prefix=/usr/local/axis2c --with=/usr/local/axis2c/include/axis2-1.6.0

#Compile Ubuntu 14.04LTS

```
./autogen.sh
./configure --with-axis2=/usr/local/axis2c/include/axis2-1.6.0 --prefix=/usr/local/axis2c

make && make install
```

#Configuration module 

$AXIS2C_HOME/modules/sandesha2

```
<module name="sandesha2" class="sandesha2">

    <Description>
        This module implements WS-ReliableMessaging for Axis2C. This implements both the WSRM submitted spec and the new spec being developed under the OASIS WSRX group.
    </Description>
    
    <inflow>
        <handler name="SandeshaGlobalInHandler" class="sandesha2">
            <!-- Global In handler should come before instance dispatching -->
            <order phase="PreDispatch" />
        </handler> 
        <handler name="SandeshaInHandler" class="sandesha2">
            <order phase="RMPhase"/>
        </handler>
    </inflow>

    <outflow>        
        <handler name="SandeshaOutHandler" class="sandesha2">
            <order phase="RMPhase"/>
        </handler>   
    </outflow>
    
    <INfaultflow>        
        <handler name="SandeshaGlobalInHandler" class="sandesha2">
            <!-- Global In handler should come before instance dispatching -->
            <order phase="PreDispatch" />
        </handler> 
        <handler name="SandeshaInHandler" class="sandesha2">
            <order phase="RMPhase"/>
        </handler>
    </INfaultflow>
    
    <OUTfaultflow>        
        <handler name="SandeshaOutHandler" class="sandesha2">
            <order phase="RMPhase"/>
        </handler>   
    </OUTfaultflow>

    <operation name="RMInOnlyOperation" mep="http://www.w3.org/2004/08/wsdl/in-only">
        <!-- namespaces for the 2005-02 spec -->
        <actionMapping>http://schemas.xmlsoap.org/ws/2005/02/rm/TerminateSequence</actionMapping>
        <actionMapping>http://schemas.xmlsoap.org/ws/2005/02/rm/SequenceAcknowledgement</actionMapping>
        <actionMapping>http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse</actionMapping>
        <actionMapping>http://schemas.xmlsoap.org/ws/2005/02/rm/AckRequested</actionMapping>
        <actionMapping>http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage</actionMapping>

        <!-- namespaces for the 2007-02 spec -->
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/SequenceAcknowledgement</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/AckRequested</actionMapping>
        
     </operation>
 
     <operation name="RMInOutOperation" mep="http://www.w3.org/2004/08/wsdl/in-out">
        <!-- namespaces for the 2005-02 spec -->
        <actionMapping>http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence</actionMapping>

        <!-- namespaces for the 2007-02 spec -->
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</actionMapping>
        <actionMapping>http://docs.oasis-open.org/ws-rx/wsmc/200702/MakeConnection</actionMapping>
        

    </operation>

   <!-- Database name parameter -->
   <parameter name="sandesha2_db" locked="false">/tmp/sandesha2_db</parameter>
   <!-- General parameters -->
   ```

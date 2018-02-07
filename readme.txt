
 
%function [affected_nodes, A1] = cascade(A0, facet_node, affected_nodes)

%  Let's think about information flow in a directed network system.
%
%  If an facet node is locked or attacted by an accident,
%  a bunch of nodes would not be received any information flow.
%
%  This program is to find a list of nodes
%  that is affectected by an attact or malfunction of a facet node.
%   
%  Input
%    A0             : adjacency matrix
%    facet_node     : node number to lock or to make malfuncting.
%
%  Output 
%    affected nodes : list of nodes that is affected by locking the
%    facet=cascade set
%  
%    A1             : adjacency matrix after removing out-flow connections
%
%  IMPORTANT!!
%    Please do not INSERT the third input argument when you use.
%    Please do not RECEIVE the second output argement when you use.
%    That is because the third input argument and second output arguments 
%    are only used for a recursive operation of CASCADE function.


Follow steps
% Install two files, in_degrees.m and cascade.m in the same folder and set working directory to the foler in matlab.
% 1. Example in the manuscript "Identification of critical connectors in local connectivity and between modules in the directed biological network" 
%run
    G = zeros(7,7);
    G(1,2)=1; G(1,3)=1; G(1,4)=1; G(2,4)=1; G(3,4)=1; G(4,5)=1; G(5,6)=1; G(6,7)=1; G(7,6)=1;
    affected_nodes = cascade(G,1)
    cascade_number=length(affected_nodes)
 
% 2. To get the list of the cascade numbers of all nodes of the example. 
%run   
    list_of_cascade_number=zeros(1,7);
    for i=1:7 
       affected_nodes = cascade(G,i);
       list_of_cascade_number(1,i)=length(affected_nodes);
    end 
    list_of_cascade_number
# javascrypt
A GUI JavaScript diagramming tool, based on Joint.js, used for making functional crypto algorithm diagrams.

backbone.js - The backbone of joint.js, this shouldn't need to be touched

hello.html - Basic demo of blocks and connectors. This file is merely an example of joint.js in action

joint.css - The styles for joint.js

joint.js - The actual library for making nice, connectable flowchart diagrams


joint.shapes.logic.js - This is an extension of joint.js which adds logic gate functionality.
                        This is the file we will be editing most! We will be adding our 'lego logic blocks' here.
                        See EXAMPLE.md for information on how to add a new block.
                        
                        
jquery.js - The always lovable jQuery library

lodash.js - Lodash is another javascript library which joint.js takes advantage of

logic.css - The styles of the logic gates and wires. This should likely remain unchanged.

logic.html - The proof of concept itself. This page shows how an addition block would work, 
             an output block, and how the numeric value of a block can be dynamic.
             
           

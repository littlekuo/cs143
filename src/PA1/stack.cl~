(*
 *  CS164 Fall 94
 *
 *  Programming Assignment 1
 *    Implementation of a simple stack machine.
 *
 *  Skeleton file
 *)


class List {
   -- Define operations on empty lists.
   isNil() : Bool { true };
   head()  : String { { abort(); "0"; } };
   tail()  : List { { abort(); self; } };

   cons(i : String) : List {
      (new Cons).init(i, self)
   };

};


class Cons inherits List {
   car : String; -- The element in this list cell
   cdr : List;	-- The rest of the list

   isNil() : Bool { false };
   head()  : String { car };
   tail()  : List { cdr };

   init(i : String, rest : List) : List {
      {
	 car <- i;
	 cdr <- rest;
	 self;
      }
   };
};



class StackCommand {
    stack : List;

    execute(str : String) : Object{
        if(str = "x") then {
            self;
        } else
        if(str = "e") then 
        {   
            if(stack.isNil()) then 0 else

            -- No error handling
            if(stack.head() = "+") then 
            {
                stack <- stack.tail();
                let op1 : Int <- (new A2I).a2i(stack.head()) in {
                       stack <- stack.tail();
                       let op2 : Int <- (new A2I).a2i(stack.head()) in {
                            stack <- stack.tail().cons((new A2I).i2a(op1 + op2));
                       };
                };
            } else 
            if(stack.head() = "s") then {
                stack <- stack.tail();
                let str1 : String <- stack.head() in {
                    stack <- stack.tail();
                    let str2 : String <- stack.head() in {
                        stack <- stack.tail().cons(str1).cons(str2);
                    };
                };
            }
            else 0
            fi fi fi;
            getStr();
        } else 
        if(str = "d") then {
             print_stack(stack);
             getStr();
        } else {
            stack <- stack.cons(str);
            getStr();
        } 
        fi fi fi
    };


    getStr():Object {
        let str : String <- (new IO).in_string() in {
           execute(str);
        }
    };

    print_stack(l : List) : Object {
      if l.isNil() then (new IO).out_string("\n")
                   else {
                         (new IO).out_string(l.head());
                         (new IO).out_string("\n");
                          print_stack(l.tail());
		           }
      fi
   };

   init () : Object {
       stack <- new List
   };

};




class Main inherits IO {
   
   command : StackCommand;

   main() : Object {
     {
      command <- new StackCommand;
      command.init();
      command.getStr();
     }
   };

};



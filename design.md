0. We believe that the user should be able to execute whatever they want.
   Does circle lang allow this? yes. Just write (what you want to execute) and it will be executed.

1. Contrary to Crcl's author's view that parameters are ugly, we believe that there should be a shorter way to pass parameters than putting them on an **implicitly agreed-on stack**
   Some options of syntax to do this is
   - to declare an array (( (F_name); expr; expr; ...)) which will be executed by the language. This vastly simplify the call site.
   - to use the access operator: (F_name) ( argument_array ). This, however  is not supported as the language itself does not support indexing by array (only by number)
   - to explicitly introduce a new primitive to the language to support this: e.g. call(F_name, arguments). We, however, don't like the idea of arbitrarily extending the language
     and would like to introduce as few new primitives into the language as possible.
   So option 1, in our humble opinion, is the most sensible.
   What about the function developer, however? from inside the function they have no way to access to the array containing this "function".
    One option is that the user will still have to pass the argument array in explicitly; Let's examine the syntax of this

  From the user's perspective:
    (__sc_args) = # Argument array;
    (F_name);

  From the developer's perspective:
    (F_name) = ((
      (V + 1x1);
      (V) := (V) + 1x1;
      ( (V) ) (_args) := (__sc_args);
      
      #...
    ))

  How is this better than explicitly passing the arguments in a stack pointer? this abstract away the stack pointer from the user; they don't have to worry about the pointer arithmetic.
  What is the tradeoff? The user now rely on (_args).

  Now, there is a very nice way to handle this: introducing a new directive (as in C macros)

  ! directive_name 
  
  **Every directive will output an object**
  **Directives can have arguments**
  **Directives' arguments can have (possibly null) name**
  **Capture **
  **Pipe operator** -> 
  

 implement a **call** operator based on Crcl's primitives
     (Call) =  ((
       //


       # 


  Directive

  using executable = array | assignment_statement | null; // other types has no effects when executed
  using evaluable = array | statement | number;
  pair<array | null, expression | null> generate_code()

  Component {
    pair<executable | null, evaluable | null> generate_code()
  }

  syntax: 
  ^ directive_name [
      dir_name: component(capture(square | curly))
      keyword_name_: keyword(string_value | regex)
      
  ]
  . [
    # code generation instruction
    .directive 
    ? directive
    
  ]
  ? [
    # evaluable expression generation instruction
    
  ]

  ^ 

  ^ while [
      condition: component(capture(square))
      body: component(capture(curly))
      
    ] {
    }

  C++ representation: 
    

  ^ while [stop_condition, body]:
  . {
    
  }

3. There should a primitive for library developers to ensure that no one overwrite their functions
6. Shorter autobreak primitive
   We decide to use the stack pointer 

  @if ( ) { }
  else ( ) { }
  else { }

  { } : returns a **Scope** which is just the 
  

2. Subroutines
   SC uses (Sc_stack_ptr) to implement the subroutine primitive
   The syntax for the declaration of the subroutine should be 

1. Conditional execution
   cond_exe(expr, expr) 

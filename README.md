This application is a Excel Clone.



=> LOGIC OF THE FORMULLA IMPLEMENTATION

    * Identify the formulla from the formulla bar.
    * Evaluate the Formulla. -> then value will come. method * used-> evaluate()
    * Reflect the value in UI
    * Update the cell value and formulla in the Database. * * method used-> setFormulla()
    * Update the childeren array in the parent.

    CONSTRAINTS:
        * Formulla is only set by the formulla bar.
        * In Formulla we have to give space in each token so that we can split the formulla via space.
    
    
    
    Possible edge cases if we change the Formulla  :-

    case 1: If the One formulla is depends on only one block.
        So, if we change the value later of any cell so it will also change the value of the dependent cell by formulla 
        Example :- 
        address -> A1         value -> 10
        we have Applied formulla in   B1  ->   ( 4 + A1)
        Value of B1 -> 14

        Later if we change the value of A1  -> 20
        then the value Of B1 should be modified with  -> 24


    case 2: 

        Example : if,
            A1 -> 10   
            B1 -> 20   (Derived by the formulla ( 2 * A1) )    
            
            C1 -> 40 (Derived by the formulla ( 2 * B1 ) )

            Later If we change the value of A1 then the value of B1 and C1 should also change.
            A1 -> 5  ( we have changed the value of A1)
            B1 -> 10  (changed value ny formulla )
            C1 -> 20  (changed value ny formulla )

        LOGIC TO BE IMPLEMENT in Case 2 :

            * If value is changed in the cell -> Then we will   update the value of that cell.
            * Then pass the message to their children which are stored in children array of that object.
            * Then ReEvaluate the formulla.
            * Then Run the code Recursively so that all the branch who are depend to each other should update their value.

        case 3:
            After Implementing the case 2 if we set the value in case of the formulla then it should not forward to the next childrens.

            Example :-
                In case of B1 if we directly change the value so it should not pass to its children.
            
            LOGIC TO BE IMPLEMENTED IN CASE 3 : 
                * if Formulla is present and we change the value then  clear the formulla
                * remove yourself from your parents array children.


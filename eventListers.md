--------------------------------------------------------------
## Event Listeners
--------------------------------------------------------------

### for adding functions to event listeners:

    in a given component:
        const functionHandler = () => {console.log('hi)}

        return (
            <button onClick={functionHandler}>text</button>
        ) 
        
has to recive functions, it doesn't just executes some code it HAS to be a function, also it passes as a reference, not execution [it's functionHandler, not functionHandler()] 

--------------------------------------------------------------

### for adding functions with params to event listeners:

    in a given component: 

        const testHandler = (param, param2) => {
                console.log(param, param2)
            }

        return (
            <button onClick={() => {handlerOfTestHandlers(1, 2)})>test</button>
            ) 
            
to pass params within a function on an event listener you have to pass a function that has a callback or a "running" function as part of the execution to be able to pass the parameters without executing the function (notice how unlike a function reference, a function with parameters is passed inside an anonymous function and that anon is the reference function)

### if you neeed to run multiple example:

    const handlerOfTestHandlers = (param, param2, param3, param4, param5, param6) => {
        testHandler(param, param2)
        testHandler2(param3, param4)
        testHandler3(param5, param6)
    } 
    
you can group functions inside a handler and call it the same way with multiple params

--------------------------------------------------------------


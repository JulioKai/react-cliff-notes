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

**if you neeed to run multiple example:**

    const handlerOfTestHandlers = (param, param2, param3, param4, param5, param6) => {
        testHandler(param, param2)
        testHandler2(param3, param4)
        testHandler3(param5, param6)
    } 
    
you can group functions inside a handler and call it the same way with multiple params

--------------------------------------------------------------

### for forms and listening events:

    <form onSubmit={handlerForDataInsideThisForm}>
        <button type='submit'>text</button>
    </form>

if a button is press insdide a form with a type submit or not defined type but its inside a form, or an input type submit, the form element will emit the event submit so it's recommended to use that event to listen instead of the onClick in the button

**don't forget to call the prevent default in the submit:**

    const submitHandler = (e) = {
        e.preventDefault()
        //rest of the logic
    }

other option to do this is passing the type=button to the button but a consecuence is not being able to submit the form with a press of an enter

--------------------------------------------------------------

### Child to Parent Communication (bottom-up):

    parent: 
        const handlerFunctionAsProp = (infoWantedFromComponentAsParameter) => {
            console.log(infoWantedFromComponentAsParameter)
            const result = infoWantedFromComponentAsParameter
        }

        return (
            <CustomComponent onCustomEventName={handlerFunctionAsProp} />
        )

if you create a function thar recives params and pass it as a pointer on a "custom event listener" to a child, the function can be executed in the child with the necesary info but will be accesed in the parent component where the function is defined

    children:
        const info = 'some info'

        const otherHandler = () => {
            props.onCustomEventName(info)
        }

        return (
            <button onClick={otherHandler}>send info</button>
        )

the function pointer can be called with props. and the name given to the custom event, in this case `props.onCustomEventName` and passing parameters or doing something in this component with the pointer (inside a function or an effect or a handler or as an event listener function, etc), will be available in the parent where the function is defined

**working example:**

component1:

    import { useState } from "react"
    import Test from "./TestComponent"

    const Game = () => {

        const [testMessage, setTestMessage] = useState('estado inicial')
        
        const randomHandler = (message) => {
            setTestMessage(message)
        }

        return (
            <div>
                <h1>waiting...</h1>
                <Test onTest={randomHandler} />
                <p>{testMessage}</p>
            </div>
        )
    } 

    export default Game

component 2:

    const Test = (props) => {

        const message = 'hello my friend'

        const clickHandler = () => {
            props.onTest(message)
        }

        return (
            <button onClick={clickHandler}>test button</button>
        )
    }

    export default Test

--------------------------------------------------------------


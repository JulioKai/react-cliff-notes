--------------------------------------------------------------
### Props
--------------------------------------------------------------

**passing props from parent to children component:**

    parent:
        <Element propName='value' propName2='value2' />

    component:
        const Element = (props) => {
            return (
                <p>{props.propName1} {props.propName2}</p>
            )
        } 
        
recives props as an argument and can be used as propierties of the object that recives as argument

--------------------------------------------------------------

**creating a wrapper or passing other jsx elements into a component:**

    parent where is called: 
        <CompContainer>
            <h1>someTitle</h1>
            <p>someParagraph</p>
        </CompContainer>

    component:
        const CompContainer = (props) => {
            return (
                <div class="some stylishing classses for ex">{props.children}</div>
            )
        } 
        
recives props as arguments, uses the reserved propierty of props called children to indicate where the nested html elements will go (the h1 and p for ex)

--------------------------------------------------------------

**passing things like classes or functions to a child component:**

    parent: 
        <Button className='clase1 clase2' onClick={someCBFunction} text='texto del boton'/>

    component: 
        const Button = (props) => {
            const classes = 'clase3' + props.className
            return (
                <button className={classes} onClick={props.onClick}> props.text </button>
            )
        } 
        
they have redifined inside the custom component inside the corresponding atribute 

--------------------------------------------------------------

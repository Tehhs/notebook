# Children tying to manage their own state 

The below code isn't great - You have a child copying parent state, and then trying to manage that copied state. This becomes an issue when the parent want's to change 
props sent into the child. Those new props will not populate into the child's state.

```jsx

const ChildElement = ({state}) => { 
    const [innerState, setInnerState] = useState(state)

    const _onItemClick = (clickedId) => { 
        const newInnerState = [...innerState]
        newInnerState.find( item => item.id == clickedId)?.selected = true 
    }
    
    return <div>
        {
            state?.map( (item, itemIndex) => 
                <div key={itemIndex} onClick={()=>{_onItemClick(item.id)}}>
                    {item.name} {item.selected == true && "(clicked)"}
                </div>
            )
        }
    </div>
}

const ParentElement = ({state}) => { 
    const [state, setState] = useState([
        {id: 1, name: "John", selected: false},
        {id: 1, name: "Alex", selected: false}
    ])

    return <ChildElement state={state}/>
}

```

A workaround to this would be changing the innner state based off changes to props

```jsx

const ChildElement = ({state}) => { 
    const [innerState, setInnerState] = useState(state)

    useEffect(()=>{
        setInnerState(state)
    }, [state])

    ...
}
```

But now you have more issues. Every time the parent re-renders, props will change, re-setting any inner state.

While this could work, if you intellegently manage how the inner state changes in response to prop changes, it's still not a great approach. 

## A better solution

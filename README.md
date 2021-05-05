# WeSplit
Simple check splitting app: project from Hacking with Swift, this is my first iOS application.

## Demo
<img src="https://dendev.net/Demos/WeSplit2.gif"/>

## Notes
#### Under the hood:
These are the variables that allow the app to save user inputs to be used in the later calculations along with default values and available tipping options.
```swift
    @State private var checkAmount = ""
    @State private var numberOfPeople = 0
    @State private var tipPercent = 2
    
    let tipOptions = [0, 10, 15, 20, 25]

```
The calculations below take the variables above and calculates a split check including tip, 
it is then returned to be displayed using calculatedCost("total") for the total amount per person, or
calculatedCost("tip") to get only the tip value. 

```swift
    func calculatedCost(_ type: String) -> Double {
        let people = Double(numberOfPeople + 2)
        let tip = Double(tipOptions[tipPercent]) / 100
        let amount = Double(checkAmount) ?? 0
        if type == "total" {
            return amount * (1 + tip) / people
        } else if type == "tip" {
            return amount * tip
        }
        return 0
    }
```

## Credit
Check out this project at [Hacking with Swift](https://www.hackingwithswift.com/100/swiftui)

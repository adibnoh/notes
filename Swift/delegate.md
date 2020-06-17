# Delegate

Delegate allow child class to instruct parent method

## Define Protocol

Can define anywhere, but usually define in parent.

```objc

// Parent.swift

protocol ParentDelegate {
    func pickUpChild()
}

```

## Parent Class

* Conform Protocol

```objc

class ParentClass: ParentDelegate {

}

```

* Declare Method to Sastify Protocol

```objc

class ParentClass: ParentDelegate {

	func pickUpChild() {

	}

}

```

* Attach `self` during navigation

```objc

class ParentClass: ParentDelegate {

	func navigateToChild() {
		let ChildClassView = self.storyboard?.instantiateViewController(withIdentifier: "ChildClassView") as! ChildClass
		ChildClassView.delegate = self
        self.navigationController?.pushViewController(ChildClassView, animated: true)
	}

}

```

## Child Class

* Declare delegate variable

```objc

class ChildClass {
	var delegate:ParentDelegate?
}

```

* Invoke parent method

```objc

class ChildClass {
	var delegate:ParentDelegate?

	func triggerDelegateMethod() {
		self.delegate?.pickUpChild()
	}
}

```
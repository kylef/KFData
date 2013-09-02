# KFData

[![Build Status](https://travis-ci.org/kylef/KFData.png?branch=master)](https://travis-ci.org/kylef/KFData)

Lightweight Core Data wrapper for iOS5+/OS X 10.7+.

## Overview

Normally you would create a single `KFDataStore` across your whole application,
(or across a whole managed object model). You can call methods on a
`KFDataStore` instance to create a `NSManagedObjectContext` or perform blocks
of code with a `NSManagedObjectContext`.

``` objective-c
KFDataStore *dataStore = [[KFDataStore alloc] init];

// You can use helper methods to perform a write or read block
[dataStore performWriteBlock:^(NSManagedObjectContext*)managedObjectContext {
    Person *kylef = [Person createInManagedObjectContext:managedObjectContext];
    [kylef setName:@"Kyle Fuller"];
}];
```

``` objective-c
// Get a managed object context for the UI
NSManagedObjectContext *managedObjectContext = [dataStore managedObjectContext];

// Perform some changes then save
[managedObjectContext performBlock:^{
    Person *kylef = [Person createInManagedObjectContext:managedObjectContext];
    [kylef setName:@"Kyle Fuller"];
    [managedObjectContext save:nil];
}];
```

## Installation

[CocoaPods](http://cocoapods.org) is the recommended way to add
KFData to your project.

Here's an example podfile that installs KFData.

### Podfile

```ruby
platform :ios, '5.0'

pod 'KFData'
```

Note the specification of iOS 5.0 as the platform; leaving out the 5.0 will
cause CocoaPods to fail with the following message:

> [!] KFData is not compatible with iOS 4.3.

## Contributing

Please see our [contributing](CONTRIBUTING.md) guide for details.

## License

KFData is released under the BSD license. See [LICENSE](LICENSE).


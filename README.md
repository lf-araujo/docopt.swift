![build status](https://travis-ci.org/docopt/docopt.swift.svg)
``docopt.swift`` is a Swift port of [docopt](https://github.com/docopt/docopt), now Linux compatible.
======================================================================

**docopt.swift** helps you create most beautiful command-line interfaces *easily*. This project is a friendly fork of the docopt team original work, but which compiles on Linux and is also [Marathon](https://github.com/JohnSundell/Marathon) compatible. 

I made little changes to the project, forked from @samdeane original [PR](https://github.com/docopt/docopt.swift/pull/14). A minimally working example looks like:


```swift
import Foundation
import Glibc
import Docopt // marathon: /home/luis/Dropbox/Documentos/Coding/Swift/docopt.swift

let doc : String = """
Not a serious example.

Usage:
  calculator_example.py <value> ( ( + | - | * | / ) <value> )...
  calculator_example.py <function> <value> [( , <value> )]...
  calculator_example.py (-h | --help)
  
Examples:
  calculator_example.py 1 + 2 + 3 + 4 + 5
  calculator_example.py 1 + 2 '*' 3 / 4 - 5    # note quotes around '*'
  calculator_example.py sum 10 , 20 , 30 , 40
  
Options:
  -h, --help
"""
var args = CommandLine.arguments
args.remove(at: 0)

print(args)
let result = Docopt.parse(doc, argv: args, help: true, version: "1.0")
print("Docopt result: \(result)")
```

Installation
======

Swift:
- Check out `docopt.swift`
- Add `docopt` folder to your project

Swift Package Manager:
```swift
.package(url: "https://github.com/lf-araujo/docopt.swift", from: "0.0.1"),
```

Or even easier, simply write a marathon script and add the following to the beginning of it:

```swift
import Docopt // marathon: https://github.com/lf-araujo/docopt.swift
```

License
======
`docopt.swift` is released under the MIT License.

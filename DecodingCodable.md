# Decoding Codable
**Ellen Mey** -
[*@el_is_for_ellen*](https://twitter.com/el_is_for_ellen) -
from Detroit Labs

#### What JSON Parsing looked like pre Swift 4
* Huge conditional binding statements.
* Even on structs with small numbers, there were tons of lines of code just to bind, map, encode, and decode.

#### What it looks like in Swift 4 with Codable
* The whole decoding process takes place on basically one line of code.
* Encoding works pretty much the same way.
* Magic
    * Codable automatically handles your intialization and mapping.

#### Customizing it to your needs
* Custom Coding Keys
    * Create an enum that conforms to String and `CodingKey`
    * Create cases for all the keys, and then simply override the default value of the ones where the key on the backend differs from the case name.
* Containers
    * Keyed (like dictionaries) and unkeyed (like arrays) containers
    * Mutable
    * Containers allow us to manipulate data in between JSON and encoding/decoding.
    * Overriding any encoding means you have to then handle all the values.
* Pro tip: If your type will only ever be encoded or decoded, conform to just `Encodable` or `Decodable` rather than both, to save you time and effort and overhead.

#### Ways to deal with less than perfect JSON structures
* **`keyDecodingStrategy`**
    * Decoders (or maybe just `JSONDecoder`) have a `keyDecodingStrategy` property which will allow you assign things like `.convertFromSnakeCase` for common decoding scenarios.
* Other things of note:
    * PropertyListEncoder
    * Create a custom encoder
    * dateDecodingStrategy is helpful but currently quite limited
    * Utilizing Codable with other frameworks like RxSwift

* Slides available at [here](https://github.com/eisforellen/talks).

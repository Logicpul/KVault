# KVault

KVault is a secure key-value storage for Kotlin Multiplatform projects. It acts as an iOS Keychain wrapper and implements encrypted SharedPreferences for Android.

## Import

```kotlin
sourceSets {
    val commonMain by getting {
        dependencies {
            implementation("com.liftric:kvault:<version>")
        }
    }
}
```

## How-to

### Init

#### Android

```kotlin
val store = KVault(context, "<fileName>")
```

| Parameter           | Description                         |
| :------------------ | :---------------------------------- |
| fileName (optional) | Name of the shared preferences file |

#### iOS

```kotlin
val store = KVault("<serviceName>", "<accessGroup>")
```

| Parameter              | Description                         |
| :--------------------- | :---------------------------------- |
| serviceName (optional) | Used to categories objects          |
| accessGroup (optional) | Used to share objects between apps  |

### Setting

```kotlin
val stringStored: Boolean = store.set(key = "LEET", stringValue = "1337")
val intStored: Boolean = store.set(key = "ANSWER", intValue = 42)
val floatStored: Boolean = store.set(key = "PI", floatValue = 3.14)
```

#### Supported Types

- String
- Int
- Long
- Float
- Double
- Bool
- ByteArray

### Getting

```kotlin
val stringValue: String? = store.string(forKey = "PASSWORD")
val intValue: Int? = store.int(forKey = "SECRET")
```

To check if an object is stored you can use:

```kotlin
val existsObject: Boolean = store.existsObject(forKey = "PASSWORD")
```

To check for which keys objects are stored:

```kotlin
val allKeys: List<String> = store.allKeys()
```

### Deleting

#### Single object

```kotlin
val isRemoved: Boolean = store.removeObject(forKey = "PASSWORD")
```

#### All objects

```kotlin
val isCleared: Boolean = store.clear()
```

## License

KVault is available under the MIT license. See the LICENSE file for more info.

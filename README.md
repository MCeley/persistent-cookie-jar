# persistent-cookie-jar

[![Build Status](https://app.bitrise.io/app/4f79c411b0998adc/status.svg?token=mTH5J1i62Bd4jMAr-Fs1jA&branch=master)](https://app.bitrise.io/app/4f79c411b0998adc)

[![](https://jitpack.io/v/MCeley/persistent-cookie-jar.svg)](https://jitpack.io/#MCeley/persistent-cookie-jar)

A persistent CookieJar implementation based on [PersistentCookieJar](https://github.com/franmontiel/PersistentCookieJar) by [franmontiel](https://github.com/franmontiel).

## Download

### Step 1. 

### Prior to Gradle 7.0: 
Add the JitPack repository in your root `build.gradle` at the end of `repositories`:
```groovy
allprojects {
    repositories {
        ...
        maven { url "https://jitpack.io" }
    }
}
```

### Gradle 7.0+: 
Add the JitPack repository in your `settings.gradle` file in the `repositories` block of `dependencyResolutionManagement`:
```groovy
dependencyResolutionManagement {
    repositories {
        ...
        maven { url "https://jitpack.io" }
    }
}
```

### Step 2. 
Add the dependency in your project level `build.gradle` file.
```groovy
dependencies {
    implementation 'com.github.MCeley:persistent-cookie-jar:1.4.0'
}
```

## Usage

Create an instance of `PersistentCookieJar` passing a `CookieCache` and a `CookiePersistor`:

```java
ClearableCookieJar cookieJar = new PersistentCookieJar(
    new SetCookieCache(), 
    new SharedPrefsCookiePersistor(context)
);
```

Then just add the `CookieJar` when building your `OkHttpClient`:

```java
OkHttpClient okHttpClient = new OkHttpClient.Builder()
                .cookieJar(cookieJar)
                .build();
```

## License

    Copyright 2016 Francisco José Montiel Navarro
    Copyright 2022 Michael Celey

    Work is derivative of PersistentCookieJar:
    https://github.com/franmontiel/PersistentCookieJar

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        https://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

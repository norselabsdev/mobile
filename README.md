## Alternative Go Mobile

Use it to compile multiple `.AAR` files for further use in Android Project.

### Initialize your go module

* Initialize your module by running `go mod init <ModuleName>`
* Replace original Go Mobile remote repo by executing `go mod edit -replace=golang.org/x/mobile@latest=github.com/norselabsdev/mobile@latest`

### Install modified Go Mobile

Download executable from Releases or build modified Go Mobile yourself by pulling this repo and running `go build` command.

### Compile .AAR files

Compile your `.AAR` file using modified Go Mobile executable (e.g. `gomobile bind -target=android <YourPackage> -v`)

### Import AAR into the project

Copy your `.AAR` files and `gomobile-java.jar` files into the project and configure gradle accordingly:

```gradle
//=============setting.gradle=================
dependencyResolutionManagement {
    repositories {
        flatDir {
            dirs 'libs'
        }
    }
}
//=============build.gradle(Your Application)======   
dependencies {
    implementation(name: 'AAR-1-Module-From-Gomobile', ext: 'aar')
    ...
    implementation(name: 'AAR-N-Module-From-Gomobile', ext: 'aar')
    implementation(name: 'gomobile-java', ext: 'jar')
}   
```


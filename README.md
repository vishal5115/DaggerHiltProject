# DaggerHiltProject

#Dependencies

buildscript {
    ...
    ext.hilt_version = '2.35'
    dependencies {
        ...
        classpath "com.google.dagger:hilt-android-gradle-plugin:$hilt_version"
    }
}

apply plugin: 'kotlin-kapt'
apply plugin: 'dagger.hilt.android.plugin'

dependencies {
    implementation "com.google.dagger:hilt-android:$hilt_version"
    kapt "com.google.dagger:hilt-compiler:$hilt_version"
}


#For Appliacion class

@HiltAndroidApp
class ExampleApplication : Application() { ... }

#For Activity class

@AndroidEntryPoint
class ExampleActivity : AppCompatActivity() { ... }

ViewModel (by using @HiltViewModel)


Note: The following exceptions apply to Hilt support for Android classes:
Hilt only supports activities that extend ComponentActivity, such as AppCompatActivity.
Hilt only supports fragments that extend androidx.Fragment.
Hilt does not support retained fragments.


To obtain dependencies from a component, use the @Inject annotation to perform field injection:


#Component Scopes

Application	SingletonComponent	@Singleton
Activity	ActivityRetainedComponent	@ActivityRetainedScoped
ViewModel	ViewModelComponent	@ViewModelScoped
Activity	ActivityComponent	@ActivityScoped
Fragment	FragmentComponent	@FragmentScoped
View	ViewComponent	@ViewScoped
View annotated with @WithFragmentBindings	ViewWithFragmentComponent	@ViewScoped
Service	ServiceComponent	@ServiceScoped


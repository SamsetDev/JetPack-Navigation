# JetPack-Navigation
Android JetPack is a set of android components designed with Kotlin in mind, available with Android Studio 3.2.<br>
This library provode major 4 component <br> <br>
 Navigation <br> 
DataMnager <br>
Slice <br>
Paging <br>



<h3>Navigation_graph</h3> <br>

    <fragment
        android:id="@+id/loginFragment"
        android:name="com.samset.jetpack.fragment.LoginFragment"
        android:label="fragment_login"
        tools:layout="@layout/fragment_login" >

        <argument
            android:name="title"
            android:defaultValue="@string/signupdata" />

        <action
            android:id="@+id/action_loginFragment_to_signUpFragment"
            app:destination="@id/signUpFragment" />
    </fragment>

    <fragment
        android:id="@+id/signUpFragment"
        android:name="com.samset.jetpack.fragment.SignUpFragment"
        android:label="fragment_sign_up"
        tools:layout="@layout/fragment_sign_up" >

        <argument
            android:name="signupdata"
            android:defaultValue='""' />
    </fragment>


<h3>Java code set your fragment like.</h3><br>

getSupportFragmentManager().replaceFragment(R.id.maincontainer,new YourFragment()).commit; 

<h3>Kotlin with JetPack set fragment</h3> <br>

        val navController = findNavController(mainNavigationFragment)
        NavigationUI.setupActionBarWithNavController(this, navController)
        navController.navigate(R.id.loginFragment)

<h3>JetPack set fragment and pass bundle data</h3> <br>

            val action = LoginFragmentDirections.action_loginFragment_to_signUpFragment()
            action.setSignupdata("Hello sam! How are you?")
            
            val navController = view.findNavController()
            navController.navigate(action)
            
<h3>JetPack set fragment and pass custom bundle data</h3> <br>

            infos.name="samset"
            infos.mobileNo="9811054xxx"

            val bundle = Bundle()
            bundle.putSerializable("signupdata",infos)
            
            val navController = view.findNavController()
            navController.navigate(R.id.signUpFragment,bundle)
        
        
   <h2>Developers Importent Point</h2> <br> 
   
   If you want Maintain fragment backstack then override this method in your MainActivity
   
    override fun onSupportNavigateUp()=findNavController(R.id.mainNavigationFragment).navigateUp()

   If you want  not maintain the backstack specific fragment then you add one line of code in navigation_graph like..
     
  ```   
   <fragment
       android:id="@+id/fragmentSecvond"
       android:name="com.samset.jetpacknavigation.fragments.FragmentSecond"
       android:label="fragment_fragment_secvond"
       tools:layout="@layout/fragment_fragment_secvond">
          <argument
           android:name="mydata"
           android:defaultValue="defaulttext"
           app:type="string" />
          <action
           android:id="@+id/action_fragmentSecvond_to_fragmentThird"
           app:clearTask="true"   //** add this line for clear backstack **
           app:destination="@id/fragmentThird" />
    </fragment>
    
   ```
You can also be change the action "Pop To" behavior from attribute pannel( from xml app:popUpTo="@+id/FragmentOne). This way when user will click back, he will be navigated to FragmentOne instead of the original destination.
   
     <fragment
       android:id="@+id/fragmentThird"
       android:name="com.samset.jetpacknavigation.fragments.FragmentThird"
       android:label="fragment_fragment_third"
       tools:layout="@layout/fragment_fragment_third">
         <action
          android:id="@+id/action_fragmentThird_to_fragmentFourth"
          app:destination="@id/fragmentFourth" />
         <action
          app:popUpTo="@id/action_fragmentSecond" // <b>.add this line and change pop to destination</b>
          android:id="@+id/action_fragmentThird_to_fragmentOne"
          app:destination="@id/fragmentOne" />
    </fragment>


   
 
   
more details [Blog Pages](http://samsetdev.blogspot.com/2018/07/jetpack-navigation.html). 

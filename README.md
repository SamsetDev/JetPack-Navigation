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
            
            
more details 

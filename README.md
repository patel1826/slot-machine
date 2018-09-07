# slot-machine
//MAIN ACTIVITY XML
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="@drawable/slotmachinebackground">

    <ImageView
        android:id="@+id/slot1"
        android:layout_width="76dp"
        android:layout_height="85dp"
        android:layout_marginBottom="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginRight="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.18"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <ImageView
        android:id="@+id/slot3"
        android:layout_width="76dp"
        android:layout_height="85dp"
        android:layout_marginBottom="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginRight="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.806"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <ImageView
        android:id="@+id/slot2"
        android:layout_width="76dp"
        android:layout_height="85dp"
        android:layout_marginBottom="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginRight="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/spinBtn"
        android:layout_width="107dp"
        android:layout_height="53dp"
        android:fontFamily="sans-serif-condensed"
        android:text="Spin"
        android:textAlignment="center"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.49"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.024" />


    <TextView
        android:id="@+id/totalCoin"
        android:layout_width="135dp"
        android:layout_height="35dp"
        android:fontFamily="sans-serif-condensed"
        android:text="TOTAL:100"
        android:textAlignment="viewStart"
        android:textColor="@android:color/black"
        android:textSize="28sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.98"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.97" />

    <TextView
        android:id="@+id/numCoin"
        android:layout_width="123dp"
        android:layout_height="37dp"
        android:fontFamily="sans-serif-condensed"
        android:text="BET:0"
        android:textAlignment="viewStart"
        android:textColor="@android:color/black"
        android:textSize="28sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.134"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.988" />

    <Button
        android:id="@+id/addCoin"
        android:layout_width="50dp"
        android:layout_height="50dp"
        android:background="@android:drawable/ic_input_add"
        android:backgroundTint="@android:color/black"
        android:fontFamily="monospace"
        android:textColor="?android:attr/colorPressedHighlight"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.01"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="1.0" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="224dp"
        android:layout_height="52dp"
        android:fontFamily="sans-serif-condensed"
        android:text="SPIN 2 WIN"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="40sp"
        android:textStyle="bold"
        android:typeface="monospace"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="205dp"
        android:layout_height="42dp"
        android:fontFamily="sans-serif-condensed"
        android:text="SPIN 2 WIN"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="40sp"
        android:textStyle="bold"
        android:typeface="monospace"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.012"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.019" />

</android.support.constraint.ConstraintLayout>

//MINI GAME XML (SEPARATE)

<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MiniGame"
    android:background="@drawable/slotmachinebackground">

    <ImageView
        android:id="@+id/slotImg2"
        android:layout_width="76dp"
        android:layout_height="85dp"
        android:layout_marginBottom="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginRight="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
    <TextView
        android:id="@+id/textView"
        android:layout_width="224dp"
        android:layout_height="52dp"
        android:fontFamily="sans-serif-condensed"
        android:text="MINI GAME"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="40sp"
        android:textStyle="bold"
        android:typeface="monospace"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="205dp"
        android:layout_height="42dp"
        android:fontFamily="sans-serif-condensed"
        android:text="MINI GAME"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="40sp"
        android:textStyle="bold"
        android:typeface="monospace"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.012"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.019" />
    <Button
        android:id="@+id/spin"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:text="Spin"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.176"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.708" />

    <EditText
        android:id="@+id/enterGuess"
        android:layout_width="85dp"
        android:layout_height="95dp"
        android:layout_marginBottom="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:ems="10"
        android:hint="Guess"
        android:inputType="textPersonName"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.174"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.267" />

    <TextView
        android:id="@+id/winTxt"
        android:layout_width="89dp"
        android:layout_height="124dp"
        android:layout_marginBottom="16dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:textAlignment="center"
        android:textSize="36dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.812"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.523" />

</android.support.constraint.ConstraintLayout>

// THREE BY THREE LAYOUT 

<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ThreeByThree"
    android:background="@drawable/slotmachinebackground">

    <ImageView
        android:id="@+id/slot1"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.2"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.251" />

    <ImageView
        android:id="@+id/slot3"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.8"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.251"
         />

    <ImageView
        android:id="@+id/slot2"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.251" />

    <ImageView
        android:id="@+id/slot4"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.2"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.49" />

    <ImageView
        android:id="@+id/slot6"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.8"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.49"
         />

    <ImageView
        android:id="@+id/slot5"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.49"
         />

    <ImageView
        android:id="@+id/slot7"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.2"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.73"
         />

    <ImageView
        android:id="@+id/slot9"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.8"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.73"
         />

    <ImageView
        android:id="@+id/slot8"
        android:layout_width="50dp"
        android:layout_height="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.73"
         />
    <Button
        android:id="@+id/spinBtn"
        android:layout_width="107dp"
        android:layout_height="53dp"
        android:fontFamily="sans-serif-condensed"
        android:text="Spin"
        android:textAlignment="center"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.49"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.024" />


    <TextView
        android:id="@+id/totalCoin"
        android:layout_width="135dp"
        android:layout_height="35dp"
        android:fontFamily="sans-serif-condensed"
        android:text="TOTAL:100"
        android:textAlignment="viewStart"
        android:textColor="@android:color/black"
        android:textSize="28sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.98"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.97" />

    <TextView
        android:id="@+id/numCoin"
        android:layout_width="123dp"
        android:layout_height="37dp"
        android:fontFamily="sans-serif-condensed"
        android:text="BET:0"
        android:textAlignment="viewStart"
        android:textColor="@android:color/black"
        android:textSize="28sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.134"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.988" />

    <Button
        android:id="@+id/addCoin"
        android:layout_width="50dp"
        android:layout_height="50dp"
        android:background="@android:drawable/ic_input_add"
        android:backgroundTint="@android:color/black"
        android:fontFamily="monospace"
        android:textColor="?android:attr/colorPressedHighlight"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.01"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="1.0" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="224dp"
        android:layout_height="52dp"
        android:fontFamily="sans-serif-condensed"
        android:text="SPIN 2 WIN"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="40sp"
        android:textStyle="bold"
        android:typeface="monospace"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="205dp"
        android:layout_height="42dp"
        android:fontFamily="sans-serif-condensed"
        android:text="SPIN 2 WIN"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="40sp"
        android:textStyle="bold"
        android:typeface="monospace"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.012"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.019" />

</android.support.constraint.ConstraintLayout>

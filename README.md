# slot-machine
  <TextView
        android:id= "@+id/timeTxt"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <ImageView
        android:id="@+id/slot1"
        android:layout_width="170dp"
        android:layout_height="140dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.03"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.872"
        app:srcCompat="@mipmap/ic_launcher" />

    <ImageView
        android:id="@+id/slot3"
        android:layout_width="170dp"
        android:layout_height="140dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.966"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.87"
        app:srcCompat="@mipmap/ic_launcher" />

    <ImageView
        android:id="@+id/slot2"
        android:layout_width="170dp"
        android:layout_height="140dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.872"
        app:srcCompat="@mipmap/ic_launcher" />

    <Button
        android:id="@+id/spinBtn"
        android:layout_width="84dp"
        android:layout_height="56dp"
        android:text="Spin"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.004"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.008" />

    <android.support.constraint.Guideline
        android:id="@+id/guideline"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        app:layout_constraintGuide_end="193dp" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="27dp"
        android:layout_height="30dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.68"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.00999999"
        app:srcCompat="@drawable/coin" />

    <ImageView
        android:id="@+id/imageView3"
        android:layout_width="27dp"
        android:layout_height="30dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.679"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.154"
        app:srcCompat="@drawable/coin" />

    <TextView
        android:id="@+id/totalCoin"
        android:layout_width="156dp"
        android:layout_height="34dp"
        android:text="TOTAL: 100"
        android:textAlignment="viewStart"
        android:textColor="?android:attr/colorPressedHighlight"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0" />

    <TextView
        android:id="@+id/numCoin"
        android:layout_width="100dp"
        android:layout_height="30dp"
        android:text="BET: 0"
        android:textAlignment="viewStart"
        android:textColor="?android:attr/colorPressedHighlight"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.87"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.154" />

    <Button
        android:id="@+id/addCoin"
        android:layout_width="40dp"
        android:layout_height="43dp"
        android:background="@android:drawable/ic_input_add"
        android:fontFamily="monospace"
        android:textColor="?android:attr/colorPressedHighlight"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.618"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.13" />

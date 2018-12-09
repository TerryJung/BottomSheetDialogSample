# BottomSheetDialogSample

[View to Full Source](https://github.com/TerryJung/BottomSheetDialogSample)

### Bottom Sheet Dialog 만들기



![Modal Bottom Sheet](https://github.com/TerryJung/TIL/blob/master/20181128/img/BottomSheet.gif?raw=true)

Bottom Sheet 를 만드려면 안드로이드 디자인 서포트 라이브러리를 추가해야합니다. 

build.gradle 에 아래와 같이 추가해주세요.

```groovy
implementation 'com.android.support:design:27.1.0'
```



그리고 BottomSheetDialogFragment 를 상속받은 Dialog class 를 제작합니다.

```java
public class BottomSheetDialog extends BottomSheetDialogFragment {
    public static BottomSheetDialog getInstance() { return new BottomSheetDialog(); }

    @Nullable
    @Override
    public View onCreateView(@NonNull LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        View view = inflater.inflate(R.layout.bottom_sheet_layout, container,false);

        return view;
    }
}
```

BottomSheetDialog 오브젝트를 받아와서 아래와 같이 .show() 를 호출하면 

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);



        FloatingActionButton fab = (FloatingActionButton) findViewById(R.id.fab);
        fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                BottomSheetDialog bottomSheetDialog = BottomSheetDialog.getInstance();
                bottomSheetDialog.show(getSupportFragmentManager(),"bottomSheet");
            }
        });

    }
}
```

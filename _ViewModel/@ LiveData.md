___

`LiveData`는 **수명 주기를 인식하는(Lifecycle-aware) 관찰 가능한(Observable) 데이터 홀더** 클래스입니다.

- **수명 주기 인식 (Lifecycle-aware):** `LiveData`는 `Activity`, `Fragment` 등 안드로이드 컴포넌트의 수명 주기 상태를 인지합니다. 이는 UI 컴포넌트가 활성 상태(STARTED 또는 RESUMED)일 때만 데이터 업데이트를 전달하고, 비활성 상태일 때는 업데이트를 일시 중지하거나 건너뛰어 **메모리 누수(memory leaks)나 불필요한 크래시를 방지**합니다.
    
    - 예를 들어, `Activity`가 백그라운드로 이동하여 `onStop()` 상태가 되면, `LiveData`는 더 이상 업데이트를 전달하지 않습니다. `Activity`가 다시 포그라운드로 오면(예: `onResume()`), 최신 데이터를 다시 전달합니다.
        
- **관찰 가능 (Observable):** `LiveData`는 데이터가 변경될 때마다 등록된 관찰자(Observer)에게 알림을 보냅니다. 이는 `ViewModel`에서 데이터를 업데이트하면 `Activity`나 `Fragment`가 자동으로 최신 데이터를 받아 UI를 갱신할 수 있게 해줍니다.
    
- **데이터 홀더 (Data Holder):** 단순히 데이터를 담고 있는 컨테이너 역할을 합니다. `MutableLiveData`는 데이터를 변경할 수 있는 `LiveData`의 서브클래스이며, `ViewModel` 내부에서 주로 사용됩니다.
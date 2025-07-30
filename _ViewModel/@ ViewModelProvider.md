___
### 1. `new ViewModelProvider(this)`

- **`ViewModelProvider`**: Android Jetpack Architecture Components 중 하나로, `ViewModel` 객체를 생성하고 관리하는 역할을 합니다. `ViewModel`은 `Activity`나 `Fragment`의 수명 주기(Lifecycle)와 독립적으로 데이터를 유지해야 하므로, 개발자가 직접 `new MainViewModel()`과 같이 인스턴스를 생성하는 것이 아니라 `ViewModelProvider`를 통해 관리하도록 합니다.
    
- **`this`**: 여기에 전달되는 `this`는 주로 **`Activity` 또는 `Fragment`의 인스턴스**를 의미합니다. `ViewModelProvider`는 이 `Activity` 또는 `Fragment`의 **수명 주기를 기반으로 `ViewModel`의 스코프(범위)를 결정**합니다.
    
    - **Activity의 `this` (예: `new ViewModelProvider(this)`)**: 이렇게 하면 `MainViewModel` 인스턴스는 해당 `Activity`가 살아있는 동안(즉, `Activity`가 `onDestroy()`되기 전까지) 유지됩니다. 화면 회전 등으로 `Activity`가 재생성되어도 동일한 `MainViewModel` 인스턴스를 얻게 됩니다.
        
    - **Fragment의 `this` (예: `new ViewModelProvider(this)`)**: 이렇게 하면 `MainViewModel` 인스턴스는 해당 `Fragment`가 살아있는 동안 유지됩니다.
        
    - **Fragment에서 `requireActivity()` 또는 `getActivity()` (예: `new ViewModelProvider(requireActivity())`)**: 이렇게 하면 `Fragment`가 속한 `Activity`의 수명 주기를 따르는 `ViewModel`을 얻게 됩니다. 이 경우, 해당 `Activity`에 속한 여러 `Fragment`가 동일한 `ViewModel` 인스턴스를 공유하여 데이터를 주고받을 수 있게 됩니다.
        

### 2. `.get(MainViewModel.class)`

- **`.get()`**: `ViewModelProvider` 인스턴스에서 특정 `ViewModel` 클래스의 인스턴스를 요청하는 메서드입니다.
    
- **`MainViewModel.class`**: 얻고 싶은 `ViewModel`의 클래스 타입입니다. `ViewModelProvider`는 이 클래스 타입에 해당하는 `ViewModel` 인스턴스를 제공합니다.
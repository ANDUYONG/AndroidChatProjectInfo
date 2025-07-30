___

### `observe()` 메서드란?

`observe()` 메서드는 `LiveData` 객체의 핵심적인 메서드입니다. 이 메서드를 사용하여 특정 `LiveData` 객체에 **관찰자(Observer)를 등록**합니다.

구문은 다음과 같습니다: `liveData.observe(lifecycleOwner, observer)`

- **`lifecycleOwner`**: 관찰자의 수명 주기를 제어하는 `LifecycleOwner`입니다. 일반적으로 `Activity`나 `Fragment`의 `this`를 전달합니다. `LiveData`는 이 `LifecycleOwner`가 활성 상태일 때만 관찰자에게 업데이트를 보냅니다. `LifecycleOwner`가 `DESTROYED` 상태가 되면, `LiveData`는 자동으로 관찰자를 제거하여 메모리 누수를 방지합니다.
    
- **`observer`**: `LiveData`의 데이터가 변경될 때 실행될 코드를 정의하는 콜백 인터페이스입니다. 람다식 `profileList -> { ... }`가 바로 이 `Observer`의 구현입니다. `LiveData` 내부의 데이터가 변경될 때마다 이 람다식이 실행되며, 변경된 데이터가 `profileList` 매개변수로 전달됩니다.
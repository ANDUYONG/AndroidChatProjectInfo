___

RecyclerView.Adapter 특정 `ViewHolder` 타입을 제네릭으로 받습니다.
그리고 List<T>형태의 값을 생성자로 받고, 그 목록은 화면 상에 보여지기 위한 데이터들 로서 관리됩니다. 좀 더 정확히 말하면 **데이터를 관리하고, 각 데이터 항목을 어떤 `ViewHolder`에 연결(바인딩)해야 하는지 지시하는 역할**입니다.

Adapter는 List로 저장한 값들을 ViewHolder에게 전달할 거고, ViewHolder들은 실제로 각각의 값들을 화면에 표시해주는 역할을 합니다.

 -**`Adapter`의 역할 (특히 `onBindViewHolder` 메서드):** 어댑터는 `RecyclerView`로부터 "몇 번째 아이템을 화면에 보여줘야 해?" 라는 요청을 받으면, 자신이 가지고 있는 `List<ProfileData>`에서 해당 `position`의 `ProfileData` 객체를 가져옵니다. 그리고 이 `ProfileData` 객체를 해당 아이템의 `ViewHolder`(`onBindViewHolder` 메서드의 `holder` 인자)에게 "이 데이터를 이 뷰 홀더에 표시해줘!" 하고 전달합니다.
    
- **`ViewHolder`의 역할 (특히 `onBindViewHolder` 내부에서 `holder`가 하는 일):** `ViewHolder`는 `item_friend.xml`과 같이 실제 화면에 표시될 각 아이템 뷰의 구성 요소들(TextView, ImageView 등)을 가지고 있습니다. 어댑터로부터 `ProfileData`를 전달받으면, `ViewHolder`는 그 `ProfileData` 객체에서 필요한 정보(예: `profile.getNickName()`, `profile.getStatusMsg()`)를 추출하여 자신의 뷰 구성 요소들(예: `nameTextView`, `statusMessageTextView`)에 직접 설정하여 **실제로 화면에 표시(렌더링)하는 역할**을 수행합니다.
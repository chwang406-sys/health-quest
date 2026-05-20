// 1. 고등학생이 교실이나 집에서 쉽게 할 수 있는 15가지 행동 미션 배열
const missions = [
    "🪑 의자에 바르게 앉아 양손을 머리 뒤로 깍지 끼고 기지개를 쫙 켜보세요. (10초)",
    "👀 지금 바로 화면에서 눈을 떼고, 먼 곳을 15초만 바라봐 주세요!",
    "🙆‍♂️ 양손을 어깨에 올리고 뒤에서 앞으로, 앞에서 뒤로 부드럽게 원을 그려보세요. (각 5회)",
    "정면을 본 상태에서 오른쪽 귀가 오른쪽 어깨에 닿는 느낌으로 고개를 지긋이 숙여보세요. 반대쪽도 진행합니다. (각 5초)",
    "허리를 곧게 펴고 양팔을 아래로 툭 떨어뜨린 뒤, 어깨를 으쓱했다가 툭 내려놓으세요. (5회)",
    "발목을 부드럽게 시계 방향, 반시계 방향으로 돌려 가며 풀어주세요. (각 5회)",
    "두 손을 앞으로 뻗어 가볍게 주먹을 쥐었다가 쫙 펴는 행동을 반복해 보세요. (10회)",
    "의자 등받이를 잡고 허리를 왼쪽, 오른쪽으로 가볍게 돌려 뒤를 바라보세요. (각 5초)",
    "숨을 깊게 들이마시며 가슴을 활짝 열었다가, 천천히 내쉬며 몸의 긴장을 풀어주세요. (3회)",
    "손목을 가볍게 털어주며 오랫동안 필기하거나 타이핑하느라 쌓인 피로를 날려보세요. (10초)",
    "양손을 깍지 끼고 앞으로 쭉 뻗으면서 등을 동그랗게 말아 시선은 배꼽을 봐주세요. (10초)",
    "자리에서 잠시 일어나 발뒤꿈치를 들었다 내렸다 하며 종아리 근육을 깨워주세요. (10회)",
    "🧘 눈을 감고 코로 숨을 들이마시며 5까지 세고, 입으로 천천히 내쉬며 긴장을 풀어보세요. (3회)",
    "💺 의자에 앉은 채로 한쪽 무릎을 양손으로 가슴 쪽으로 끌어당겨 허리와 엉덩이를 늘려주세요. 반대쪽도 해보세요. (각 10초)",
    "🤸 양팔을 옆으로 쭉 펴고 작은 원부터 큰 원까지 천천히 그리며 어깨와 팔 주변을 풀어주세요. (각 방향 5회)"
];

// 2. HTML에서 제어할 요소(Element)들을 가져오기
const missionText = document.getElementById("mission-text");
const missionCard = document.getElementById("mission-card");
const btnRandom = document.getElementById("btn-random");
const btnComplete = document.getElementById("btn-complete");
const btnReset = document.getElementById("btn-reset");
const completedCountEl = document.getElementById("completed-count");
const counterLabel = document.querySelector(".counter-label");

// 3. 상태 변수 설정 (완료 횟수 기억)
let completedCount = 0;
let currentMissionIndex = -1;

// 4. [새 미션 뽑기] 버튼 클릭 이벤트
btnRandom.addEventListener("click", () => {
    let randomIndex;

    // [연속 중복 방지] 이전에 나왔던 미션과 연속으로 똑같은 미션이 나오지 않도록 방지
    do {
        randomIndex = Math.floor(Math.random() * missions.length);
    } while (randomIndex === currentMissionIndex);

    currentMissionIndex = randomIndex;

    // 카드에 미션 텍스트 적용 및 스타일 다듬기
    missionText.textContent = missions[currentMissionIndex];
    missionText.classList.remove("default-text"); // 안내문 스타일 제거

    // 미션 완료 버튼 활성화
    btnComplete.disabled = false;

    // [바운스 초기화] 카드가 통통 튀는 애니메이션이 매번 재실행되도록 처리
    missionCard.classList.remove("bounce");
    void missionCard.offsetWidth; // 강제 리플로우(Reflow)로 애니메이션 초기화
    missionCard.classList.add("bounce"); // 버그 수정 완료!
});

// 5. [미션 완료!] 버튼 클릭 이벤트
btnComplete.addEventListener("click", () => {
    // 완료 횟수 1 증가
    completedCount += 1;

    // 화면에 증가된 횟수 반영
    completedCountEl.textContent = completedCount;

    // 한 번 완료한 미션은 연속으로 완료할 수 없도록 버튼을 다시 비활성화
    btnComplete.disabled = true;

    // 15개 미션을 모두 완료했을 때 종료 멘트를 보여줍니다
    if (completedCount >= missions.length) {
        // 새 미션 뽑기 버튼 비활성화
        btnRandom.disabled = true;

        // 카드에 종료 축하 메시지 표시
        missionText.textContent = "🏆 대단해요! 오늘의 스트레칭 미션 15개를 모두 완료했어요! 몸도 마음도 한결 가벼워졌을 거예요. 내일 또 함께 해요 💪";
        missionText.classList.remove("default-text");

        // 완료 횟수 라벨을 축하 문구로 변경
        counterLabel.textContent = "🎊 오늘 목표 달성!";

        // 리셋 버튼을 화면에 나타냅니다
        btnReset.style.display = "block";
    } else {
        // 아직 남은 미션이 있을 때는 일반 완료 메시지 표시
        missionText.textContent = "🎉 멋져요! 몸이 한결 편안해졌기를 바랍니다. 다음 미션도 도전해 보세요!";
        missionText.classList.add("default-text");
    }
});

// 6. [처음부터 다시 하기] 버튼 클릭 이벤트
//    모든 상태를 초기화해서 앱을 처음 상태로 되돌립니다.
btnReset.addEventListener("click", () => {
    // 상태 변수 초기화
    completedCount = 0;
    currentMissionIndex = -1;

    // 완료 횟수 숫자 초기화
    completedCountEl.textContent = 0;

    // 카운터 라벨 원래대로 복구
    counterLabel.textContent = "✨ 오늘 내가 해낸 미션!";

    // 미션 카드 안내 문구 초기화
    missionText.textContent = "아래 버튼을 눌러 새로운 스트레칭 미션을 확인하세요!";
    missionText.classList.add("default-text");

    // 버튼 상태 초기화
    btnRandom.disabled = false;
    btnComplete.disabled = true;

    // 리셋 버튼 다시 숨기기
    btnReset.style.display = "none";
});

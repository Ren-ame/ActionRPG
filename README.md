# ActionRPG

현재 상황
=========
1. 기본적인 wasd 이동과 점프
2. ~~캐릭터 모델링 에셋을 구해 fbx로 변환 (스켈레톤이 달라 기존에 쓰이던 ABP, Anim 파일이 적용이 안되어 리타겟팅 시도 -> 실패 -> 리타겟팅 방법을 찾는 중)~~
3. 애니메이션을 추출하여 블렌더로 얻는 뽑아내는 방법 -> 추출한 애니메이션 FBX를 임포트 -> 애니메이션 ABP, 블렌드 스페이스 만들기
4. CCharacterManager, CSwappableCharacter 생성 -> CCharacterManager를 통해 현재 필드에 나와있는 캐릭터를 컨트롤, CSwappableCharacter를 상속받아 각각 캐릭터 생성


현재 목표
=========
캐릭터 3개 완성해서 변경까지 가능하게 만들어 보기

문제점
======
어째서인지 FBX로 넣은 애니메이션들이 EnableRootMotion을 켜지 않으면 캐릭터의 크기, 회전 등 매우 작아진다 왜 그러는지 모르겠다...
캐릭터 스켈레톤을 블렌더로 FBX내보내기 하면 왜인지 스켈레톤에 아마추어까지 달라 붙어서 언리얼에서 보면 Root 본 위에 아마추어가 한층 더 있어서 리타겟이 안되는거 같다

# ActionRPG

현재 상황
=========
1. 기본적인 wasd 이동과 점프
2. ~~캐릭터 모델링 에셋을 구해 fbx로 변환 (스켈레톤이 달라 기존에 쓰이던 ABP, Anim 파일이 적용이 안되어 리타겟팅 시도 -> 실패 -> 리타겟팅 방법을 찾는 중)~~
3. 애니메이션을 추출하여 블렌더로 얻는 뽑아내는 방법 -> 추출한 애니메이션 FBX를 임포트 -> 애니메이션 ABP, 블렌드 스페이스 만들기
4. CPlayerController, CSwappableCharacter 생성 -> CPlayerController를 통해 현재 필드에 나와있는 캐릭터를 컨트롤, CSwappableCharacter를 상속받아 각각 캐릭터 생성
5. 캐릭터 애니메이션 변경 및 공격 애니메이션
![image](https://github.com/user-attachments/assets/d2f00cb0-16e9-4e4e-9832-8df9552785df)
![image](https://github.com/user-attachments/assets/bfda90d5-723f-4085-b3e4-8b2755fa63f8)   
6. 루트모션을 이용한 이동을 사용하고싶은데   
![image](https://github.com/user-attachments/assets/5b886cdf-4c15-4a24-abde-7a1e0d229dcc)
사진처럼 루트모션이 땅속으로 박혀 아래로 내려가는 문제가 있다. 루트모션의 방향을 변경하고싶어서 인터넷에서 찾아보는 중이다. 이거 못고치면 공격시 이동이 이상하게 적용되어서 굉장히 슬플것 같다 따흐흑...
7. 캐릭터 변경이 어렵다 메쉬를 바꿔야하는건가 아니면 다른 캐릭터들의 visible만 끄는건가... 캐릭터 변경도 DataAsset으로 관리를 해야하는건가...?
8. 캐릭터 변경 코드 작성 중
   애니메이션 루트 방향을 어떻게 바꾸는지 아직도 모르겠다 커브를 이래저래 만져보고있지만 원하는 대로 이동이 되지않는다...
9.   
   ![image](https://github.com/user-attachments/assets/ef2b0091-6c09-4fb8-bae3-7797ad79ff46)
   ![image](https://github.com/user-attachments/assets/0291630c-e1ee-4a1a-b5c9-abd075d588e3)
   이익!!!!!!!! 캐릭터를 Possess로 전환할때 카메라가 이렇게 박혀버린다... 캐릭터에서 카메라를 생성하지 않고 컨트롤러에서 생성해야하나싶다.
   



현재 목표
=========
캐릭터 3개 완성해서 변경까지 가능하게 만들어 보기

문제점 및 궁금증
======
어째서인지 FBX로 넣은 애니메이션들이 EnableRootMotion을 켜지 않으면 캐릭터의 크기, 회전 등 매우 작아진다 왜 그러는지 모르겠다...   
캐릭터 스켈레톤을 블렌더로 FBX내보내기 하면 왜인지 스켈레톤에 아마추어까지 달라 붙어서 언리얼에서 보면 Root 본 위에 아마추어가 한층 더 있어서 리타겟이 안되는거 같다   

추가로 비주얼 스튜디오 상대경로 넣는 방법을 까먹었다...   
프로젝트->프로퍼티->VC++ 디렉터리->포함 디렉터리->../ 추가 이게 아니였나?

~~점프 모션이 안보인다 이건 또 왜 이럴까... 굉장히 슬프다 머리가 아퍼... 점프에서 루프 모션으로 가는 부분만 나와서 더 머리가 아프다...~~   
~~공격모션도 안나온다! 행복해! 즐거워!~~   
그보다 더 어려운건 캐릭터를 CSwappableCharacter를 상속받아서 만들 때 스킬을 어디에 만들어야 할지 모르겠다... 예전 프로젝트처럼 DoAction을 만들고 평타 스킬모션 전부 거기에 넣어야 하나?   
그냥 CSwappableCharacter에 평타 q,e,r 만들고 캐릭터 별 cpp에 상속 받아서 만들면 안되나? 뭐가 좋은지 뭐가 되는지를 잘 모르겠다...
-> 이건 아직도 잘 안된다...

~~너무 애니메이션에서 시간을 잡아먹는 것 같다...~~  애니메이션 고쳤다!   
스킬관리도 너무 어렵다 데이터 에셋으로 한다면 캐릭터를 변경할 때 데이터 에셋이 변경되어야 할텐데 그때마다 데이터 에셋을 변경할 수 있는 건가? ~~이것 때문에 메쉬만 바꾸는 것은 안될꺼 같기도 하고...~~   
~~결국 상속받은 캐릭터 3개를 캐릭터 변경시 불러오는게 맞는 것 같은데 아휴 어렵기도 하지 내가 왜 괜히 주제를 이걸로 정해선...~~~   
-> CPlayerController에서 
![image](https://github.com/user-attachments/assets/8c6b1fa2-975a-48ba-8037-e3310f33f564)   
이런식으로 CSwappableCharacter를 상속받은 캐릭터를 CPlayerController에서 UPROPERTY(EditDefaultsOnly) 이런식으로 블루프린트에서 넣으려고 했지만 액터 생성전 하드 참조는 안된다길래 소프트 참조를 하기위해 TSoftObjectPtr를 사용했더니   
![image](https://github.com/user-attachments/assets/7f084ecb-062e-4939-a264-bdade9d15201)   
이것처럼 월드 상에 모든 오브젝트를 넣을 수 있던데 이것도 액터, 캐릭터 또는 CSwappableCharacter를 상속받은 것만 넣을 수 있는 방법이 있나 찾아보는 중이다.

![image](https://github.com/user-attachments/assets/443177bc-249e-4b07-944a-04c8e41c45ca)   
플레이어 스타트가 있어서 시작하면 
![image](https://github.com/user-attachments/assets/05041256-7cc2-4891-8770-864c2e5b0d17)   
위 사진처럼 캐릭터가 하나 더 생성된다 그래서 플레이어 스타트를 지웠더니
![image](https://github.com/user-attachments/assets/9fac0edf-3379-4889-a70d-e141c6402b29)  
이 사진처럼 공중에서 생성되어있다 왜 그러는지는 
                                            ![XX-W9_YQV1h2dJBNdqTrNWTVd-8H3iHgaYrToeoYm7PIScV5VZHwjPmw9K3VJ4puuYfiuIirNqtaRz0eWoDs3Q](https://github.com/user-attachments/assets/d4ff1a0f-b436-4858-819c-50d17cd37825)




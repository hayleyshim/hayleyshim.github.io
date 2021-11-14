---
title: "[NFT]3.NFT Storage Service 적용 기술"
tags: [nft]
author: hayley
---
<html>
    <head>
        <body>
        <font size="4" color="purple" >
          <div>1편 <a href="https://hayleyshim.github.io/blog/nftstorage1">'NFT가 Infra 시장에 가져올 변화'</a>, 2편 <a href="https://hayleyshim.github.io/blog/nftstorage2">'NFT Storage Service'</a>에 이어 <b>NFT Storage Service의 작동 방식 및 적용 기술</b>에 대해 알아보자.
        <br><br>
        <font size="4" color="black">
        <p>우선, NFT Storage의 작동 방식은 다음과 같다.
        <br><br>
        <p>	
        <p><b>1. 콘텐츠 주소 지정(Content Addressing)</b> : 사용자가 NFT.Storage에 데이터를 업로드하면 CID 라고 하는 콘텐츠의 IPFS 해시를 받는다 . CID는 데이터의 고유한 지문이며 저장 방법과 위치에 관계없이 콘텐츠를 참조하는 데 사용할 수 있는 범용 주소이다. CID는 콘텐츠 자체에서 생성되기 때문에 CID를 사용하여 NFT 데이터를 참조하면 취약한 링크 및 "러그 풀(rug pull)" 과 같은 문제를 방지할 수 있다 .
        <p><b>2. 증명 가능 스토리지(Provable Storage)</b> : NFT.Storage는 장기 분산 데이터 저장을 위해 Filecoin을 사용한다. NFT 데이터를 장기적으로 보존하기 위해 저장 및 검색 거래를 중개한다. Filecoin은 시간이 지남에 따라 NFT 데이터의 내구성과 지속성을 보장하기 위해 암호화 증명을 사용하는 영구 계층을 제공한다.
        <p><b>3. 탄력적인 검색(Resilient Retrieval)</b> : IPFS 및 Filecoin을 통해 저장된 이 데이터는 공용 IPFS 게이트웨이 를 통해 브라우저에서 직접 가져올 수 있다 .
        <p><img src="https://filecoin.io/uploads/screen-shot-2021-04-29-at-1-51-42-pm.png" align="center"> 
        <p><span style="display: inline-block; width: 98%; text-align: center;"><b>NFT Storage 작동 방식</b>    
        <br><br>  
        <p> <font size="4" color="black">NFT Storage 서비스에 적용된 기술을 알아보자
        <p>  
        <p><b>1. Content Addressing</b>
        <p>-  NFT Storage의 콘텐트 주소 지정(Content Addressing) 개념을 알고 개인적으로 흥미로웠다. 대학원 때 연구 주제로 삼았던 정보 중심 네트워크(Information Centric Network)의 IP기반이 아닌 주소 기반 통신 체계를 연상하게 하는 개념이었기 때문이다. 이미 <a href="https://github.com/ipfs/notes/issues/375">IPFS github에 이 둘의 상관 관계에 대한 질문</a>이 있었다. 하지만 ICN과 IPFS는 몇 가지 주요 차이점이 있다.
        <p>
        <p>- ICN과 IPFS의 주요 차이점
        <p><blockquote>1. ICN/NDN은 종종 링크 계층에 있는 반면 IPFS는 응용 프로그램 계층에 있으며 링크 및 전송 계층에서 사용할 수 있는 모든 것을 활용한다.
        <p>2. 암호화 주소 지정은 ICN/NDN 스택의 핵심 원시적이지 않다. ICN/NDN은 전달된 데이터가 요청된 데이터임을 확인할 수 있는 방법이 없다(HTTP와 비슷하다).
        <p>3. ICN/NDN은 라우팅 설정 방법을 결정하는 제어 지점에 의존한다.
        <p>4. IPFS는 노드 이탈에 매우 탄력적이고 ICN/NDN 네트워크는 링크 계층에 너무 가깝기 때문에 그렇지 않다.
        <p>5. IPFS는 안전한 변경 가능한 포인터를 위해 SFS의 자체 인증 명명(SFS)을 사용한다. ICN/NDN은 이를 전파하기 위해 제어 지점에 의존한다.
        <p>6. 안타깝게도 ICN/NDN 세계는 공공 및 권한 없는 네트워크에 초점을 맞추지 않았기 때문에 검증 가능성과 신뢰할 수 없는 상호 작용보다는 제어 신뢰가 많은 설계이다.</blockquote>         <p>
        <p>- NFT Storage 에서 Content Addressing 개념은 콘텐트 를 찾는 데 사용되는 키가 콘텐트 자체에서 파생되는 정보 시스템에서 데이터를 구성하고 찾는 기술이다. 
        <p>- 예를 들어 다음과 같은 링크를 해결할 때 어떤 일이 발생하는지 보자. "nftschool.dev/concepts/content-addressing" 
        <p>- 먼저 운영 체제는 여러 도메인으로 분할된 전역 공유 키-값 저장소를 쿼리한다. DNS는 네트워크 카드가 네트워크를 통해 HTTP 요청을 보내는 데 사용할 수 있는 IP 주소를 반환한다. 여기서 이 사이트의 명명 규칙은 키 /concepts/content-addressing를 응답 페이로드로 전환한다 .
        <p>- nftschool.dev/concepts/content-addressing 과 같은 주소의 모든 구성요소는 변할 수 있다(mutable). 모든 것은 변하고 동적인 웹의 context 상에서 이는 당연한 방식이다. 결과적으로 우리는 Link rot에 대해 알고 있다.  
        <p>- 대부분의 NFT는 실제로 링크일 뿐이므로 Link rot은 NFT에 영향을 미친다. 보통 비용 문제로 NFT 내부에 오프체인 데이터에 대한 링크만 저장하기 때문에 접근할 수 없는 링크(Link rot)와 함께 NFT를 저장하면 블록체인 기록이 변경되지 않은 상태로 유지되더라도 NFT의 가치가 손상된다.
        <p>- 따라서, NFT에서 오프체인 자산으로 안전하게 연결하려면 안전한 링크가 필요한데 콘텐트 주소 지정은 정확히 필요한 종류의 링크를 제공한다. 
        <p>- 콘텐츠 주소 지정 시스템은 키-값 저장소처럼 작동하지만 한 가지 중요한 차이점이 있다. 더 이상 키를 선택할 수 없다는 것이다. 대신 키는 동일한 콘텐츠에 대해 항상 동일한 키를 생성하는 결정적 함수를 사용하여 저장된 값에서 직접 파생된다.
        <p>- 키와 값을 받는 대신 put메서드는 값을 가져와 호출자에게 키를 반환한다. 자신의 키를 선택할 수 없는 대가로 귀중한 속성을 얻을 수 있다.
        <br><br>
        <p><b>2. 콘텐트 주소 지정을 사용하는 방법 'IPFS'</b>
        <p>- 콘텐트 주소 지정을 실제 활용하여 내구성 있는 링크가 있는 NFT를 만드는 방법이다.
        <p>- 가장 간단한 방법은 IPFS 를 사용하는 것dl다. 데이터가 IPFS에 저장되면 사용자는 복사본이 있는 모든 IPFS 노드에서 데이터를 가져올 수 있으므로 데이터 전송을 보다 효율적으로 수행하고 단일 서버의 부하를 줄일 수 있다. 각 사용자는 데이터 조각을 가져올 때 나중에 요청할 수 있는 다른 사용자를 돕기 위해 로컬 복사본을 보관한다.
        <p>- IPFS 란? IPFS는 파일, 웹 사이트, 응용 프로그램 및 데이터를 저장하고 액세스하기 위한 분산 시스템이다. 즉, 피어 투 피어(p2p) 스토리지 네트워크로 IPFS를 이해하는데 세 가지 기본 원칙이 있다.
        <p><blockquote> 1) 콘텐츠 주소 지정을 통한 고유 식별
        <p> 2) 방향성 비순환 그래프(DAG)를 통한 콘텐츠 연결
        <p> 3) DHT(분산 해시 테이블)를 통한 콘텐츠 검색</blockquote>
        <br><br>
        <p><b>3. 콘텐트 지속성을 위한 'Filecoin'</b>
        <p>- Filecoin을 IPFS와 함께 사용하면 콘텐츠 지속성을 위한 인센티브 계층과 콘텐츠 주소 지정에 대한 IPFS의 솔루션을 결합하여 완벽한 솔루션을 제공한다. IPFS는 명확한 감사 추적 없이 시간이 지남에 따라 콘텐츠가 변경될 수 없도록 하여 URL이 해결되지 않는 문제를 해결한다. Filecoin은 콘텐츠를 계속 검색할 수 있도록 하여 IPFS에서 제공하는 콘텐츠 기반 주소 지정이 시간이 지나도 복원력을 유지하도록 한다.
        <p>Filecoin은 novel cryptography, consensus protocols, and game-theoretic incentives 통해 이 임무를 달성한다.  간단히 말해서 Filecoin 네트워크에 저장된 데이터를 위한 진정한 분산형 스토리지다. 
        <p>Filecoin의 스토리지 검증 시스템은 탈중앙화 스토리지에 대해 이전에 다루기 어려웠던 문제를 해결한다. Filecoin과 같은 분산 네트워크에서 신뢰를 유지하려면 네트워크 자체에 대한 신뢰를 구축할 방법이 필요하다. 이를 위해 Filecoin의 분산 네트워크에서 검증된 스토리지를 제공하려는 사람은 두 가지를 증명해야 합니다. 첫 번째는 올바른 데이터 세트가 주어진 스토리지 공간에 저장되고 두 번째는 동일한 데이터 세트가 지속적으로 저장된다는 것이다. 
        <p>Filecoin의 증명 알고리즘 이 이를 처리한다. Proof-of-Replication 은 주어진 스토리지 제공자가 클라이언트의 원본 데이터의 물리적으로 고유한 복사본을 저장하고 있음을 증명하는 반면, Proof-of-Spacetime 은 클라이언트의 데이터가 시간이 지남에 따라 지속적으로 저장된다는 것을 증명한다.
        <p>이 증명 시스템 외에도 Filecoin 네트워크는 게임 이론적인 인센티브에 의존하여 악의적이거나 부주의한 활동을 억제한다. 모든 Filecoin 저장소 제공자는 제공자가 되기로 동의할 때 Filecoin 토큰(FIL)의 형태로 담보를 제공해야 한다. 시공간 증명(Proof-of-Spacetime) 검사에 실패한 스토리지 제공자는 처벌을 받고 담보물의 일부를 잃게 되며 결국 다시 고객에게 스토리지를 제공할 수 없게 된다. Filecoin 네트워크는 지속적으로 성장하여 콘텐츠 지속성, 콘텐츠 주소 지정 스토리지에 대한 용량이 빠르게 증가하고 있다. 
        <p>
        <p>다음 편에서는 NFT Storage Service가 가져올 <b>비지니스 가치</b>에 대해 알아보자.
        <br>
        <br> <font size="5" color="purple"><b>[Reference]
        <p><a href="https://nft.storage/">NFT Storage 
        <p><a href="https://nftschool.dev/">NFT School    
        <p><a href="https://ipfs.io/">IPFS 
        <p><a href="https://filecoin.io/">Filecoin 




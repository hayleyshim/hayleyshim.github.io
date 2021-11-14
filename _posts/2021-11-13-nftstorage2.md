---
title: "[NFT]2.NFT Storage Service"
tags: [nft]
author: hayley
---
<html>
    <head>
        <body>
        <font size="5" color="purple" >
        <div>1편 <a href="https://hayleyshim.github.io/blog/nftstorage1">'NFT가 Infra 시장에 가져올 변화'</a>에 이어 <b>NFT 시대를 위한 Infra 서비스</b>를 알아보자.
        <font size="5" color="black">
        <br>
        <p> <font size="5" color="black"><b>기존 NFT Storage 서비스는 어떤 것이 있나</b>
        <br><br><a href="https://nft.storage/"><img src="https://nft.storage/images/logo-nft.storage.svg" style="width: 70%; height: 70%;" align="center"></a>
        <p><span style="display: inline-block; width: 100%; text-align: center;"><b> < NFT Storage > </b>
        <font size="5" color="black">
        <p>- NFT Storage는 사용자가 NFT 콘텐트와 메타데이터를 원활하고 안전하게 저장할 수 있도록 한다.
        <p>- 데이터는 <b>IPFS, Filecoin</b> 상에 분산화된 형태로 저장되고 Smart Contract에서 사용되는 콘텐트 주소 기반 <b>IPFS URI</b>를 사용하여 참조된다. 
        <br><br>
        <p>하지만 현재 NFT Storage Service에 대해 다양한 문제가 제기되고 있다.
        <br><br>
        <p><b> 문제점</b>  
        <p>	
        <span style="font-size:15pt; font-style:italic">'원본과 사본을 구별하지만 원본 복제나 해킹, 소실을 막진 못한다. 물리적 원본이 존재하는 그림이나 조각상과 달리 디지털 자산 자체는 얼마든지 <b>무단 복제 문제</b>가 불거질 수 있다.' - 출처 : 대체불가토큰(NFT), 전자신문(2021.11.11)</span>
        <br><br>
        <span style="font-size:15pt; font-style:italic">'NFT 콘텐츠 자산이 블록체인 외부에 저장되기 때문에 원본 파일에 대한 해킹 등에 의한 훼손 위험이 잔재하고 디지털 특성상 무단복제를 원천적으로 막을 수 없다는 단점은 여전하다', 'NFT화된 디지털 예술품의 보존 방식은 크게 NFT를 만든 블록체인 내 예술품 자체를 같이 저장하는 온체인(On-chain) 방식과 예술품 자체는 일반서버나 IPFS 등 블록체인 밖에 저장하는 방식이 있으며 저장용량 및 고비용 등의 이유로 후자가 대다수를 차지하는 현실이라 외부로부터 <b>원본 훼손 위험</b>이 존재한다.' - 출처 : NFT, 디지털 자산시장의 진화, KDB미래전략연구소(2021.8.30) </span>
         <br><br>
            <p>원본 파일의 <b>훼손, 무단 복제</b> 등의 문제점들을 해결하기 위해 NFT 가상 자산을 안전한 장소에 저장하는  <font size="5" color="purple" ><b>NFT Storage 서비스</b></font>가 필요할 것이다.
        <br><br> 
	<p> 실제 NFT 플랫폼에서 거래되고 있는 NFT를 살펴보자.
	<p><img src="https://github.com/hayleyshim/hayleyshim.github.io/blob/master/assets/images/nft_example.png?raw=true" align="center">
	<p>위와 같이 NFT URL 값이 노출되었고 해당 URL을 입력하면 누구나 <b>NFT 자산</b>에 쉽게 접근할 수 있다.
	<p>살펴본 것과 같이 현재 일반서버나 IPFS 등 블록체인 밖에 저장하는 On-chain 방식은 NFT 원본에 대한 <b>훼손 및 무단 복제의 위험</b>이 있기 
       때문에 향후에 이를 보완할 NFT Storage service가 필요한 시점이다. 
                
        <p><font size="5">다음 편에서는 위에 언급한 NFT Storage에 적용된 기술인<font color="purple"> <b>콘텐트 주소 지정, IPFS, Filecoin</b></font> 에 대해 자세히 알아보자.</font>
        <br>
        <br> <font size="5" color="purple"><b>[Reference]
        <p><a href="https://nft.storage/">NFT Storage

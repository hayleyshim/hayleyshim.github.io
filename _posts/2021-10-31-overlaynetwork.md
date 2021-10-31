---
title: Home NW를 Overlay NW로 구성하기
tags: [nw]
author: hayley
---
<html>
    <font size="3" color="purple"><p><b>Overlay Network란?</b>
    <p>Overlay Network는 물리 네트워크 위에 생성되는 <b>가상의 컴퓨터 네트워크</b>입니다. 
    <p>쉽게 이해하면 물리적인 네트워크는 Underlay NW이고 그것을 기반으로한 가상의 네트워크는 Overlay NW입니다.
    <p class="aligncenter">
      <img src="https://flylib.com/books/2/959/1/html/2/images/mir16f11.jpg">
    </p>  
    <center>ref) Computer and Communication Networks,2007</center>
    <p>
      
    도커 컨테이너에서 호스트들 각각에 있는 컨테이너 네트워크를 오버레이 네트워크로 연결합니다.
      <p>호스트는 동일한 서브넷에 연결되거나 그 사이에 라우터가 있는 다른 서브넷에 있을 수 있습니다.</p> 
    <p>각 컨테이너에는 추가 인터페이스가 제공되므로 IP주소가 제공되지만 모두 동일한 서브넷에 있습니다. </p>
    <p>이러한 인터페이스 간의 트래픽은 노드 간에 <b>터널링</b>되므로 각 컨테이너는 다른 호스트에 있음에도 불구하고 동일한 컨테이너 네트워크에 있는 것처럼 보입니다. </p>
    <p>예로 P2P, VPN와 비슷하게 생각할 수 있습니다. </p>
      
    <p>  
    <p>Docker 17.06부터는 오버레이 네트워크를 구성하는데 아래와 같은 방법이 권장됩니다.
    <p>  1. 네트워크 상 노드 간에 swarm network를 만듭니다
    <p>  2. 상단에 overlay network를 생성하면 swarm 노드가 자동으로 서로를 검색합니다.
    <p>     이때, 모든 Docker 호스트 노드가 서로 액세스할 수 있고 방화벽에서 터널링 포트(TCP 2377, TCP/UDP 7946, UDP 4789)가 열려있는지 확인합니다.
    <p>  
      <p>[Reference]
      <p><a href="https://archived.informaticslab.co.uk/infrastructure/2015/12/09/raspberry-pi-docker-cluster.html"> A Raspberry Pi Docker Cluster
      <p><a href="https://medium.com/@tukai.anirban/container-networking-overlay-networks-b712d6ddfb67">Container Netowkring: Overlay Networks  
      <p><a href="https://medium.com/@tukai.anirban/docker-on-raspberry-pi-getting-started-c7b403205ecf">Docker on Raspberry Pi: Getting started
      <p><a href="https://kubernetes.io/ko/docs/concepts/cluster-administration/networking/">Cluster Networking
          
          
</html>        




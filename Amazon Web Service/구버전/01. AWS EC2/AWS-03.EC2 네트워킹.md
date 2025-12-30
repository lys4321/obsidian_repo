## EC2 네트워킹 개요
- AWS에서는 EC2 인스턴스 같은 AWS 리소스를 사용하기 위하여 VPC(Virtual Private Cloud)라는 AWS 계정 전용 가상 네트워크를 제공
- EC2 인스턴스를 생성하려면 먼저 아래의 단계를 거쳐야 하며
	1. VPC를 생성
	2. VPC 내 Subnet 중 하나를 선택(게이트웨이 같은 역할)
- EC2 인스턴스가 생성될 시 만들어지는 논리적 가상 네트워크 카드인 기본 네트워크 인터페이스(ENI)는 IPv4 주소를 할당받게 되는데 이 주소는 Subnet의 IPv4 CIDR 범위에서 기본 Private IP 주소를 수신한 것이다.
- 또한 EC2 인스턴스의 ENI는 Amazon의 Public IP 주소 풀에서 Public IP 주소를 받게 되는데 이 주소는 EC2 인스터스가 중지되거나 종료될 때까지만 할당받게 됨
	- 영구적인 Public IP가 필요한 경우, AWS 계정에 Elastic IP를 할당하여 이 주소를 EC2 인스턴스나 ENI에 연결하여 사용
  => ENI는 Subnet에게 Private 주소를, Amazon Public IP에게는 Public 주소를 받아 인스턴스를 매핑하도록 한다.
-----
## EC2 네트워킹 기타 내용
- Elastic Public IP
	- 동적 클라우드 컴퓨팅을 위해 고안된 정적 IPv4 주소
	- AWS에서는 AWS 계정에 주소가 할당되며 릴리스할 떄까지 할당된 상태로 유지됨
- VPC(Virtual Private Cloud)
	- Amazon Cloud 내에서 논리적으로 격리된 가상 네트워크
	- EC2 인스턴스를 생성/실행하기 위해 준비가 되어 있어야 함
		- EC2 인스턴스는 VPC의 Subnet에서 붙으며 Subnet의 CIDR 범위에서 주소를 할당 받음
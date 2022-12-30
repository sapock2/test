
### Persistence Volume/ConfigMap/Secret
 1. EFS 생성 
   Network 에서 각 AZ별 Security groups 추가
  ![image](https://user-images.githubusercontent.com/49747084/210037806-42f1c94e-abe9-45c4-9e5c-c124c5e1bb21.png)
  
  ![image](https://user-images.githubusercontent.com/49747084/210037842-2ad25cc6-30d4-43bd-8d33-5591d5fb1627.png)


 2. ServiceAccount 생성
  default namespace 사용
  ![image](https://user-images.githubusercontent.com/121626006/210042218-a28fec1b-3035-46e3-9ecf-6055ca58be4e.png)
  ![image](https://user-images.githubusercontent.com/49747084/210038010-7421b7cb-f3d4-4ef2-b63a-379d33befcad.png)
  
3. 서비스 계정(efs-provisioner)에 권한(rbac) 설정
  ![image](https://user-images.githubusercontent.com/49747084/210038122-86a71c9e-e04d-452f-9b7d-e5ab9dd5a325.png)

 4.  EKS에 EFS Provisioner 설치
  ![image](https://user-images.githubusercontent.com/49747084/210038907-609bf464-a8e4-4ac4-9894-7bc11582331a.png)
  
  ![image](https://user-images.githubusercontent.com/49747084/210038972-9a73574d-1f4b-4de8-ae9e-33459de50ec9.png)
  
  - 생성된 Provisioner 를 StorageClass 에 등록 후 확인
   ![image](https://user-images.githubusercontent.com/49747084/210039004-ca1d25c4-ad74-4217-9e73-4e223acb3b05.png)
   
   ![image](https://user-images.githubusercontent.com/49747084/210039091-4b70c70c-fe5b-4f68-a5e6-225af00f5925.png)

 5. 해당 Provisioner 사용하는 pvc 생성 후 pvc 조회하여 확인
  ![image](https://user-images.githubusercontent.com/121626006/210041858-51bd876d-9955-44b6-8b0b-36345addcbd1.png)
 
 6. deployment.yaml 에 volume 정보 등록 
  ![image](https://user-images.githubusercontent.com/49747084/210039235-a78b8c67-fdbb-4a11-9bb0-4bf612b76c79.png)
  
  ![image](https://user-images.githubusercontent.com/49747084/210039277-f20fcaee-df2e-4222-8603-ddfd44135b04.png)

 7. 배포 후 해당 pod 에 파일시스템이 정상 마운트 되는 것 확인
  ![image](https://user-images.githubusercontent.com/49747084/210039374-6a976534-e3f4-49fe-9408-a35351ccd422.png)

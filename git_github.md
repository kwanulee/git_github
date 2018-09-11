<style> 
div.polaroid {
  	width: 640px;
  	box-shadow: 0 10px 30px 0 rgba(0, 0, 0, 0.2), 0 16px 30px 0 rgba(0, 0, 0, 0.19);
  	text-align: center;
	margin-bottom: 0.5cm;
}
</style>

# **Git과 GitHub**을 이용한 프로젝트 관리 

[**git**](https://git-scm.com/)은 소스코드의 변경을 효과적으로 관리하기 위해 개발된 '**[분산형 버전 관리 시스템](https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-%EB%B2%84%EC%A0%84-%EA%B4%80%EB%A6%AC%EB%9E%80%3F#분산-버전-관리-시스템)**'이지만, 소스코드 외에 텍스트 기반 파일의 버전관리에 널리 사용되고 있다. 

[**GitHub**](https://github.com/)는 **git**의 원격 저장소로서 협업플랫폼의 역할을 수행한다. 여기서 **저장소**란 버전관리 대상이 되는 특정한 프로젝트의 파일들을 저장하는 공간을 나타내며, 지역 저장소와 원격 저장소로 구분된다. *지역 저장소*는 현재 작업하고 있는 컴퓨터 내에 위치하는 프로젝트 파일을 저장하는 디렉토리를 의미하고, *원격 저장소*는 인터넷 상의 서버에 위치하며, 여러 **git** 클라이언트와 공유될 수 있다.

[**GitHub Desktop**](https://desktop.github.com/)은 GUI 기반의 git 클라이언트 중에 하나로, 이 문서에서는 **GitHub Desktop**를 이용하여 **Android Project**의 소스를 관리하는 두 가지 시나리오를 설명한다. 

1. [**git**을 이용한 버전관리](#1)
2. [**GitHub**을 이용한 협업하기](#2)

<a name="1"></a>
## 1. **git**을 이용한 프로젝트의 버전관리
임의의 **Project** (예, Android Project, Java Project, NodeJs Project, etc.)에 대한 버전관리 시나리오는 다음과 같다.

1. [**Project**를 위한 새로운 지역 **git** 저장소 생성](#1.1)
2. [**Project**의 일부 파일을 수정 후, 지역 **git** 저장소에 커밋(commit)](#1.2)
	- [수정사항 취소하기 (Discard changes)](#1.2.1)  
	- [**git** 저장소를 이전 커밋(commit)으로 되돌림 (*필요한경우*)](#1.2.2) 
4. [원격 **git** 저장소(**GitHub**)에 푸시(push)](#1.4)

---
###1.0 사전준비
- [**Java Project** 생성 (예, HelloJava)](start-java.html)
- [**git** 클라이언트 설치](install_git_clients.html) 
- [**GitHub** 계정 만들기](create-github-account.html)  

---
<a name="1.1"></a>
###1.1 **Project**를 위한 새로운 지역 **git** 저장소 생성
1. **GitHub Desktop** 시작화면에서 **Create new repository** 클릭
	<div class="polaroid">
		<img src="figure/github-desktop-new-repository.JPG"> 
	</div>	

	[**다른 방법**] [**File**] 메뉴에서 [**New respository..**] 클릭
	<div class="polaroid">
		<img src="figure/create-local-repository-windows.PNG">
	</div>	
	
2. 다음 정보 입력 및 선택 후 [**Create repository**] 선택
	- [**Name**]: 저장소 (프로젝트) 이름 (예, *Hello* - 이 이름의 Java Project가 생성된 것을 가정 )
	- [**Local path**]: 저장소의 위치 (예, *C:\Users\kwlee\Projects*)
	- [Git ignore]: **Java** 선택 (Git에서 버전관리되지 않는 대상 파일들을 설정한 것)
	
3. 새로운 **git** 저장소(예, *C:\Users\kwlee\Projects\Hello*)에 .git 폴더 및 .gitattributes, .gitignore 파일이 생성되어 있음을 확인할 수 있다.

---
<a name="1.2"></a>
###1.2 **Project**의 일부 파일을 수정 후, 지역 **git** 저장소에 커밋(commit)
	
**커밋(commit)**이란 하나 이상의 파일에 대한 변경을 **git** 저장소에 저장하는 것을 의미한다. 다음은 **Android Project**의 일부 파일을 수정 후, 지역 **git** 저장소에 커밋을 하는 절차를 설명한다.

1. **[Java Project]**:  **Java Project**의 일부 파일을 수정 

	예를 들어, **Hello** 프로젝트에서 *Main.java* 파일을 다음과 같이 수정
	
	```java
	public class Main {
	
	    public static void main(String[] args) {
	        int year = 2018;
	        System.out.println("Welcome to "+year+" Web&App Class");
	    }
	}
		
	```

2. **[GitHub Desktop]**: 커밋에 포함시킬 혹은 포함하지 않을 변경을 선택 하고, 커밋 메시지 작성후, [**Commit to BRANCH**] 클릭 
	
<a name="1.2.1"></a>
####1.2.1  수정사항 취소하기 (Discard changes) (*필요한 경우*)

파일을 수정하고 커밋하기 전에, 수정되기 전 상태로 돌리기

1. **[GitHub Desktop]**: **Changes** 탭의 변경된 파일 목록에서 수정전 상태로 되돌리고자 하는 파일의 오른쪽 마우스버  클릭 후, 메뉴의 **Discard changes..** 클릭 
	

<a name="1.2.2"></a>
####1.2.2 지역 **git** 저장소를 이전 커밋(commit)으로 되돌림 (*필요한 경우*)
다음은 현재 **git** 저장소를 이전 커밋 상태로 되돌리는 방법이다. 만약 여러 커밋을 되돌리고자 하는 경우에는 최신것부터 시작하여 순서대로 되돌리는 것이 좋다.

1. **[GitHub Desktop]**: **History** 탭의 커밋 목록에서 되돌리고자 하는 커밋의 오른쪽 마우스버튼  클릭 후, 메뉴의 **Revert this commit** 클릭 
	
---
<a name="1.4"></a>
###1.3 지역 **git** 저장소를 원격 저장소(**GitHub**)에 푸시(push)

1. **GitHub Desktop**에서 **GitHub** 계정에 로그인 설정 

	- **File** > **Options..** 메뉴를 클릭
	- **GitHub.com**의 **Sign in** 버튼 클릭 
	- **Sign in** 화면에서 **GitHub**의 Username과 Password 입력후 **Sign in** 클릭 
		<div class="polaroid">
			<img src="figure/signin-github.PNG">
		</div>
2. 작업중인 지역 **git** 저장소를 원격 저장소(**GitHub**)에 올리기
	- **GitHub Desktop** 화면 상단의 **Publish repository** 클릭 
	- *Keep this code private* 체크박스 선택 해제 후, [**Publish repository**] 버튼 클릭
	 	

3. 웹브라우저를 통해 **GitHub**의 원격 저장소에 지역 **git** 저장소의 내용이 동기화 되어 있는 확인  
	


## <a name="2"></a>2. **GitHub**이용한 협업하기
**GitHub**이용한 협업하기 두 명의 시나리오는 다음과 같다.

	가정
		- GitHub에 두 개의 사용자 계정(예, kwanulee, kwanu70)이 존재 
		- kwanulee/Hello 저장소가 존재
		- kwanulee/Hello 저장소를 kwanulee와 kwanu70이 공유하여 협업하고자 함

1. **kwanulee/Hello** 저장소의 Collaborator로 *kwanu70*을 추가 (참조. [가. **GitHub** 저장소에 Collaborator 추가하기](#2.1))
2. *kwanu70*은 **kwanulee/Hello** 원격 저장소의 파일을 지역 **git** 저장소로 복제 (참조. [나. **GitHub** 저장소를 복제하기](#2.2))
3. *kwanu70*은 지역 **git** 저장소로 복제된 파일을 변경/커밋하고, 이를 **kwanulee/Hello** 저장소와 동기화  (참조. [다.  복제된 **GitHub** 저장소를 수정하고 동기화하기](#2.3))
4.  *kwanulee*는 자신의 지역 **git** 저장소를 **kwanulee/Hello** 원격 저장소의 최신 상태로 동기화

<a name="2.1"></a>
### 가. **GitHub** 저장소에 Collaborator 추가하기
1. **GitHub** 저장소의 메인 화면에서 **Settings** 탭 선택

	<div class="polaroid">
			<img src="figure/github-settings.png">
	</div>

2. **Settings** 탭의 왼쪽 메뉴 중에 **Collaborators** 선택 한후, Collaborator로 추가할 **GitHub** 계정 ID (예, *kwanu70*)를 입력하고, [**Add collaborator**] 클릭

	<div class="polaroid">
			<img src="figure/github-add-collaborator.png">
	</div>

3. Collaborator로 추가한 계정 사용자의 이메일로 아래와 같은 내용의 이메일이 전송되며, **accept or decline** 링크를 클릭하여 수락을 해야함
	<div class="polaroid">
			<img src="figure/email-authentication.png">
	</div>
	
	<div class="polaroid">
			<img src="figure/accept-invitation.png">
	</div>


<a name="2.2"></a>
### 나. **GitHub** 저장소를 복제하기

1. **GitHub Desktop**의 [**File**] 메뉴에서 [**Clone respository..**] 클릭
	<div class="polaroid">
		<img src="figure/clone-file-menu-windows.png">
	</div>	
2. 저장소 복제 
	- **GitHub 사용자이름**과 복제(Clone)하려는 **GitHub 리파지토리**를 입력, (예, kwanulee/Hello)
	- 복제할  리포지토리가 저장될 로컬 패스를 지정 후, [**Clone**] 클릭 
	

<a name="2.3"></a>
### 다. 복제된 **GitHub** 저장소를 수정하고 동기화하기
1. IntelliJ IDEA IDE에서 복제된 *HelloCloned* 프로젝트를 열고, Main.java 파일을 변경

	```
	public class Main {
	   	public static void main(String[] args) {
	      		int year = 2018;
	        	System.out.println("Welcome to "+year+" Web&App Class"); // modified by Kwanu70
	   }
	}
	```

2. 커밋에 포함시킬 혹은 포함하지 않을 **변경을 선택**하고 **커밋 메시지 작성**후, [**Commit to master**] 클릭 
	
	 
5. **GitHub Desktop** 화면 우측 상단의 [**Push origin**] 버튼 클릭
		<div class="polaroid">
			<img src="figure/github-desktop-sync-button.png">
		</div>
		
6. 웹브라우저를 통해 **GitHub**의 원격 저장소에 지역 **git** 저장소의 내용이 동기화 되어 있는 확인  
7. 
	<div class="polaroid">
			<img src="figure/github-sync-result.png">
		</div>
 



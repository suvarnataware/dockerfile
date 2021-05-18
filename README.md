# sonarqube-flutter
sonarqube-flutter-dockerfile
Prerequisites	
	Flutter SDK
	Dart SDK separately
	https://github.com/insideapp-oss/sonar-flutter/releases/download/0.2.1/sonar-flutter-plugin-0.2.1.jar
SonarQube Installation	
	Download Dockerfile - https://github.com/suvarnataware/sonarqube-flutter/blob/main/Dockerfile
	Build & Run
	sudo docker build --tag sonarq .
	sudo docker run -d -p 9000:9000 sonarq
	
Sonar Scanner	
	Source: https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.3.0.2102-linux.zip
	Expand the downloaded file into the directory of your choice
	We'll refer to it as $install_directory in the next steps.
	Update the global settings to point to your SonarQube server by editing $install_directory/conf/sonar-scanner.properties:
	
	
	Add the $install_directory/bin directory to your path.
	export PATH = "$PATH:/$HOME/sonar-scanner/bin"`
	
	Verify your installation by opening a new shell and executing the command sonar-scanner
	
SonarConfiguration	
	Create a sonar-project.properties file at the root of the project :
	https://github.com/suvarnataware/sonarqube-flutter/blob/main/sonar-project.properties
	
Run Analysis	
	Download dependencies
	flutter pub get
	Run tests
	flutter test --machine > tests.output
	Compute coverage (--machine and --coverage cannot be run at once...)
	flutter test --coverage
	Run the analysis and publish to the SonarQube server ( Run this command from project directory)
	sonar-scanner
	
	
Report	If you want to download report , use webapi to get data in json format which you can convert in excel
	

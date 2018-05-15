// This shows a simple build wrapper example, using the AnsiColor plugin.

	pipeline {
		agent any
		triggers { pollSCM('* * * * *') }

		stages{

			stage('Generar desplegable') {
				steps {
					powershell 'wget http://localhost:6969/shutdown'
					powershell 'wget http://localhost:9696/shutdown'
					bat "build.bat"

				}
			}

			stage('Desplegar Integraci�n') {
				steps {
					bat "deploy-app.bat"
				}
			}
		}
		

		post {
			failure {
				mail to: 'csanchez@eknowit.com',
					subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
					body: "Something is wrong with ${env.BUILD_URL}"
			}
		}

	}

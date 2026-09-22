pipeline{
	agent any
	stages{
		stage("Checkout"){
			steps{
				echo "Connect to github"
				echo "enter the crendentials"
				echo "Select correct branch"
				echo " check the data "
			}

		}
		stage("Build"){
			steps{
				echo "move the checkout the data"
				echo "call hte maven comands"
			}

		}
		stage("Deploy"){
			steps{
				echo "Create the docker  image"
				echo "run the conainer"
			}

		}
		stage("Kubernetes"){
			steps{
				echo "Crate the kubernetes cluster"
				echo "expose the api"
			}

		}

	}
}
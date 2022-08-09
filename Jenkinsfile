pipeline {
	agent any
    label 'ubuntu' //label the machine name as which one has been created as node } 
	stages {
	stage('removing old files') {
	steps {
		sh "sudo rm -rvf /var/www/html/laravel-pos/*"
        //Deletion of the hidden file inside the folder/ append the file in production phase
		sh "sudo rm -rvf /var/www/html/laravel-pos/.git*"
		sh "sudo rm -rvf /var/www/html/laravel-pos/.e*"
		sh "sudo rm -rvf /var/www/html/laravel-pos/.s*"
		}
	}
	stage('Cloning repo') {
	steps {
		sh " cd /var/www/html/laravel-pos/"
		sh " sudo git clone https://github.com/madhavgit911/laravel.git /var/www/html/laravel-pos/"
		sh " cd /var/www/html/laravel-pos/"
		sh " ls "
		sh " cd /var/www/html/laravel-pos/"
		sh " pwd " 
		sh " sudo chmod -R 777 /var/lib/jenkins/workspace/laravel/hey.sh "
		sh " sudo ./hey.sh "
		sh " cd /var/www/html/laravel-pos/"
		sh " pwd "
		sh " sudo php artisan key:generate"
		sh " sudo php artisan migrate "
		sh " sudo php artisan db:seed "
		sh " sudo php artisan storage:link "
		//
		}
	}
	stage('Reloading code') {
	steps {
		sh " sudo chmod -R o+w /var/www/html/laravel-pos/storage/"
		sh "sudo systemctl reload nginx"
		}
	}
	}
}

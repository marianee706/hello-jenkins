pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building the application...'
      }
    }
    stage('Test') {
      steps {
        echo 'Running tests...'
      }
    }
    stage('Package') {
      steps {
        echo 'Creating package...'
        // คำสั่ง zip อาจแตกต่างกันไปขึ้นอยู่กับระบบปฏิบัติการและไฟล์ของคุณ
        // ตัวอย่างนี้จะบีบอัดไฟล์ทั้งหมดใน directory ปัจจุบัน
        sh 'zip -r my-app.zip .'
        sh 'ls -l' // เพิ่มคำสั่ง ls -l เพื่อแสดงไฟล์หลังจากการ package (แบบฝึกหัดที่ 1)
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying the application...'
      }
    }
    // เพิ่ม Stage สำหรับแสดงรายการไฟล์ (แบบฝึกหัดที่ 1)
    stage('List Workspace Files') {
      steps {
        echo 'Listing files in workspace...'
        sh 'ls -l'
      }
    }
  }
  // เพิ่มบล็อก post สำหรับแจ้งเตือน (แบบฝึกหัดที่ 2)
  post {
    always {
      echo 'This will always run after the pipeline finishes.'
    }
    success {
      echo 'Pipeline completed successfully 🎉'
    }
    failure {
      echo 'Pipeline failed ❌'
    }
    // เพิ่มการ cleanup เช่น ลบไฟล์ zip หากไม่ต้องการเก็บไว้
    // cleanup {
    //   sh 'rm my-app.zip'
    // }
  }
}

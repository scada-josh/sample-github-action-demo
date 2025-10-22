## DevOps Jenkins & GitHub Actions & N8N - Day 8

### 📋 สารบัญ

1. [Basic Github Actions](#basic-github-actions)
2. [NodeJS Express GitHub Actions](#nodejs-express-github-actions)
3. [Python Flask GitHub Actions](#python-flask-github-actions)
4. [Java Spring Boot GitHub Actions](#java-spring-boot-github-actions)
5. [NextJS GitHub Actions](#nextjs-github-actions)
6. [.NET Core GitHub Actions](#dotnet-core-github-actions)
7. [Go Fiber GitHub Actions](#go-fiber-github-actions)
8. [PHP Laravel GitHub Actions](#php-laravel-github-actions)
9. [NestJS GitHub Actions](#nestjs-github-actions)

## Basic Github Actions
> GitHub Actions คือ ระบบ CI/CD ที่ถูกพัฒนาขึ้นโดย GitHub เพื่อช่วยในการทำงานอัตโนมัติ (Automation) ต่าง ๆ เช่น การทดสอบโค้ด การสร้างและการปรับใช้แอปพลิเคชัน เป็นต้น โดย GitHub Actions ใช้ไฟล์ YAML ในการกำหนด Workflow ที่ต้องการให้ทำงานอัตโนมัติเมื่อเกิดเหตุการณ์ต่าง ๆ เช่น การ Push โค้ด หรือการสร้าง Pull Request

### ข้อดีของ GitHub Actions
- **การผสานรวมกับ GitHub**: GitHub Actions ถูกผสานรวมอย่างลึกซึ้งกับ GitHub ทำให้การตั้งค่าและการใช้งานง่ายขึ้น
- **ความยืดหยุ่น**: สามารถกำหนด Workflow ได้ตามความต้องการของโปรเจกต์
- **การสนับสนุนหลายภาษา**: รองรับการทำงานกับหลายภาษาโปรแกรมและแพลตฟอร์ม
- **ชุมชนและ Marketplace**: มีชุมชนที่ใหญ่และ Marketplace ที่มี Action สำเร็จรูปให้เลือกใช้งานมากมาย

### ข้อจำกัดของ GitHub Actions
- **ข้อจำกัดของทรัพยากร**: มีข้อจำกัดในการใช้งานทรัพยากร เช่น เวลาในการรัน Workflow และจำนวนการใช้งานฟรี
- **ความซับซ้อนในการตั้งค่า**: สำหรับโปรเจกต์ที่ซับซ้อน การตั้งค่า Workflow อาจต้องใช้ความรู้และประสบการณ์มากขึ้น
- **การจัดการ Secrets**: การจัดการ Secrets อาจมีความซับซ้อนและต้องระมัดระวังในการใช้งาน

### แพลนการใช้งาน GitHub Actions
- **Free Plan**: สำหรับผู้ใช้ทั่วไปและโปรเจกต์โอเพ่นซอร์ส มีข้อจำกัดในการใช้งานทรัพยากร
- **Pro Plan**: สำหรับนักพัฒนาที่ต้องการฟีเจอร์เพิ่มเติมและทรัพยากรที่มากขึ้น
- **Team Plan**: สำหรับทีมพัฒนาที่ต้องการการจัดการที่ดีขึ้นและฟีเจอร์เพิ่มเติม
- **Enterprise Plan**: สำหรับองค์กรที่ต้องการการสนับสนุนและฟีเจอร์ขั้นสูง

### ข้อจำกัดของ Free Plan
- **เวลารัน Workflow**: จำกัดเวลาในการรัน Workflow ต่อเดือน 2000 นาที
- **จำนวน Concurrent Jobs**: จำกัดจำนวน Concurrent Jobs ที่สามารถรันได้พร้อมกัน สูงสุด 20 งาน
- **การใช้งาน Self-hosted Runners**: จำกัดจำนวน Self-hosted Runners ที่สามารถใช้งานได้
- **การสนับสนุน**: ไม่มีการสนับสนุนทางเทคนิคจาก GitHub โดยตรง
- **การจัดเก็บ Artifacts และ Logs**: จำกัดระยะเวลาการจัดเก็บ Artifacts และ Logs 
สูงสุด 90 วัน
> Artifacts คือ ไฟล์หรือข้อมูลที่ถูกสร้างขึ้นระหว่างการรัน Workflow เช่น ไฟล์บิลด์ (build files) หรือผลลัพธ์ของการทดสอบ (test results) ซึ่งสามารถนำไปใช้ในขั้นตอนถัดไปหรือดาวน์โหลดได้หลังจากการรันเสร็จสิ้น
- **การใช้งานกับ Private Repositories**: จำกัดการใช้งาน GitHub Actions กับ Private Repositories
- **การใช้งานกับ Public Repositories**: ไม่มีข้อจำกัดในการใช้งาน GitHub Actions กับ Public Repositories
- **การใช้งานกับ Marketplace Actions**: จำกัดการใช้งานบาง Action จาก GitHub Marketplace
- **การใช้งาน Secrets**: จำกัดจำนวน Secrets ที่สามารถสร้างได้ต่อ Repository สูงสุด 100 ตัว
- **การใช้งานกับ GitHub Packages**: จำกัดการใช้งาน GitHub Packages สำหรับการจัดเก็บและเผยแพร่แพ็กเกจ
- **การใช้งานกับ GitHub Codespaces**: จำกัดการใช้งาน GitHub Codespaces สำหรับการพัฒนาโค้ดในสภาพแวดล้อมคลาวด์ 

โดยรวมแล้ว Free Plan ของ GitHub Actions เหมาะสำหรับผู้ใช้ทั่วไปและโปรเจกต์โอเพ่นซอร์สที่มีความต้องการใช้งานในระดับพื้นฐาน แต่หากต้องการฟีเจอร์เพิ่มเติมหรือทรัพยากรที่มากขึ้น อาจพิจารณาอัปเกรดเป็นแผนที่สูงขึ้น

### ตัวอย่าง Basic GitHub Actions Workflow
```yaml
name: CI
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '22'
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

### โครงสร้างของ GitHub Actions Workflow
- `name`: ชื่อของ Workflow
- `on`: เหตุการณ์ที่ทำให้ Workflow ทำงาน เช่น การ Push โค้ด
- `jobs`: งานที่ต้องการให้ทำงานภายใน Workflow
- `runs-on`: กำหนดสภาพแวดล้อมที่ใช้รันงาน เช่น `ubuntu-latest`
- `steps`: ขั้นตอนต่าง ๆ ที่ต้องการให้ทำ
  - `name`: ชื่อของขั้นตอน
  - `uses`: ใช้ Action ที่มีอยู่ใน Marketplace หรือที่สร้างขึ้นเอง
  - `run`: คำสั่งที่ต้องการรันในขั้นตอนนั้น ๆ


### เพิ่มเติมให้สมบูรณ์ยิ่งขึ้น
```yaml
# =================================================================
# GitHub Actions CI/CD Pipeline for Express.js Application
# =================================================================
# ชื่อ workflow
name: CI/CD Pipeline - Express App

# =================================================================
# TRIGGERS: กำหนดเหตุการณ์ที่จะทำให้ workflow ทำงาน
# =================================================================

# กำหนด Trigger: ให้ Workflow ทำงานทุกครั้งที่มีการ push ไปยัง branch 'main'
on:
  push:
    branches:
      - main
    # ถ้าต้องการ build ตอนแท็กด้วย ให้เปิดบรรทัดด้านล่างนี้
    # tags: [ 'v*.*.*' ]

# กำหนด Trigger: ให้ Workflow ทำงานทุกครั้งที่มีการสร้าง Pull Request ไปยัง branch 'main'
  pull_request:
    branches:
      - main

# กำหนด Trigger: แบบ Manual (Workflow Dispatch) เพื่อให้สามารถกดรันได้เองจากหน้า GitHub
  workflow_dispatch:

# =================================================================
# ENVIRONMENT VARIABLES: กำหนดตัวแปรที่ใช้ทั้ง Workflow
# =================================================================
env:
  NODE_VERSION: '22'
  DOCKER_IMAGE: 'iamsamitdev/express-app-action'  # เปลี่ยนเป็น Docker Hub username ของคุณ

# =================================================================
# JOBS: กำหนด Jobs ที่จะรันใน Workflow
# =================================================================
jobs:
  # Job 1: Build และ Test
  build-and-test:
    name: Build & Test
    runs-on: ubuntu-latest
    
    steps:
      # Step 1: Checkout code จาก repository
      - name: 📥 Checkout code
        uses: actions/checkout@v4
      
      # Step 2: ตั้งค่า Node.js environment
      - name: 🔧 Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: 'npm'
      
      # Step 3: แสดง Node.js และ npm version
      - name: 📋 Display Node.js and npm versions
        run: |
          echo "Node.js version: $(node --version)"
          echo "npm version: $(npm --version)"
      
      # Step 4: ติดตั้ง dependencies
      - name: 📦 Install dependencies
        run: |
          if [ -f package-lock.json ]; then
            npm ci
          else
            npm install
          fi
      
      # Step 5: รัน tests พร้อม coverage
      - name: 🧪 Run tests with coverage
        run: npm test
      
      # Step 6: Upload coverage report (optional)
      - name: 📊 Upload coverage report
        if: always() && hashFiles('coverage/**') != ''
        uses: actions/upload-artifact@v4
        with:
          name: coverage-report
          path: coverage/
          retention-days: 7

  # Job 2: Build และ Push Docker Image
  build-docker:
    name: Build & Push Docker Image
    runs-on: ubuntu-latest
    needs: build-and-test
    # รันเฉพาะเมื่อ push ไปยัง main branch หรือ manual dispatch
    if: github.event_name == 'push' || github.event_name == 'workflow_dispatch'
    
    steps:
      # Step 1: Checkout code
      - name: 📥 Checkout code
        uses: actions/checkout@v4
      
      # Step 2: ตั้งค่า Docker Buildx
      - name: 🔧 Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      # Step 3: Login to Docker Hub
      # หมายเหตุ: ต้องตั้งค่า DOCKERHUB_USERNAME และ DOCKERHUB_TOKEN ใน GitHub Secrets
      - name: 🔐 Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      # Step 4: สร้าง Docker image metadata (tags และ labels)
      - name: 🏷️ Extract Docker metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.DOCKER_IMAGE }}
          tags: |
            type=ref,event=branch
            type=sha,prefix={{branch}}-
            type=raw,value=latest,enable={{is_default_branch}}
      
      # Step 5: Build และ Push Docker image
      - name: 🐳 Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
      
      # Step 6: แสดง image digest
      - name: 📝 Image digest
        run: |
          echo "Image pushed successfully!"
          echo "Tags: ${{ steps.meta.outputs.tags }}"

  # Job 3: Security Scan (Optional - ต้องติดตั้ง Trivy)
  security-scan:
    name: Security Scan
    runs-on: ubuntu-latest
    needs: build-docker
    if: github.event_name == 'push' || github.event_name == 'workflow_dispatch'
    # เพิ่ม permissions สำหรับ security-events
    permissions:
      contents: read
      security-events: write
      actions: read
    
    steps:
      # Step 1: Checkout code
      - name: 📥 Checkout code
        uses: actions/checkout@v4
      
      # Step 2: รัน Trivy vulnerability scanner
      - name: 🔒 Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: ${{ env.DOCKER_IMAGE }}:latest
          format: 'sarif'
          output: 'trivy-results.sarif'
        continue-on-error: true
      
      # Step 3: Upload Trivy results to GitHub Security
      - name: 📤 Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v3
        if: always()
        with:
          sarif_file: 'trivy-results.sarif'
        continue-on-error: true

  # Job 4: Deploy (Optional - ตัวอย่างการ deploy)
  deploy:
    name: Deploy to Production
    runs-on: ubuntu-latest
    needs: [build-docker, security-scan]
    if: github.ref == 'refs/heads/main' && (github.event_name == 'push' || github.event_name == 'workflow_dispatch')
    environment:
      name: production
      url: http://your-app-url.com
    
    steps:
      # Step 1: Checkout code
      - name: 📥 Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Deploy notification
      - name: 🚀 Deploy notification
        run: |
          echo "Deploying application..."
          echo "Image: ${{ env.DOCKER_IMAGE }}:latest"
          echo "Environment: production"
      
      # Step 3: Deploy to server (ตัวอย่าง - ต้องปรับแต่งตามจริง)
      # หากใช้ SSH, ควรเพิ่ม SSH key ใน GitHub Secrets
      # - name: 🚢 Deploy to server
      #   uses: appleboy/ssh-action@master
      #   with:
      #     host: ${{ secrets.HOST }}
      #     username: ${{ secrets.USERNAME }}
      #     key: ${{ secrets.SSH_PRIVATE_KEY }}
      #     script: |
      #       docker pull ${{ env.DOCKER_IMAGE }}:latest
      #       docker stop express-app || true
      #       docker rm express-app || true
      #       docker run -d --name express-app -p 3000:3000 ${{ env.DOCKER_IMAGE }}:latest
      
      # Step 4: Success notification
      - name: ✅ Deployment complete
        run: echo "Application deployed successfully!"

```


### NodeJS Express GitHub Actions

> ตัวอย่าง CI/CD Pipeline สำหรับ NodeJS Express Application โดยใช้ GitHub Actions พร้อม Docker Build, Deploy, และ Rollback

#### 📁 โครงสร้างโปรเจกต์

```
express-docker-app/
├── .github/
│   └── workflows/
│       └── main.yml          # GitHub Actions Workflow
├── src/
│   └── app.ts               # Express Application
├── tests/
│   └── app.test.ts          # Unit Tests
├── Dockerfile               # Docker Configuration
├── package.json             # Dependencies
├── tsconfig.json            # TypeScript Config
└── jest.config.js           # Jest Test Config
```

---

### 🚀 ขั้นตอนที่ 1: สร้างโครงสร้างโปรเจกต์

1. **สร้าง Directory สำหรับ GitHub Actions Workflow**:
   ```bash
   mkdir -p .github/workflows
   ```

2. **สร้างไฟล์ Workflow**:
   ```bash
   touch .github/workflows/main.yml
   ```

---

### 📝 ขั้นตอนที่ 2: เขียน GitHub Actions Workflow

เปิดไฟล์ `.github/workflows/main.yml` และเขียนโค้ดดังนี้:

```yaml
# ชื่อของ Workflow ที่จะแสดงในหน้า Actions ของ GitHub
name: CI/CD - Express Docker App

# กำหนด Trigger Events
on:
  # รันอัตโนมัติเมื่อมี push ไปยัง branch develop หรือ main
  push:
    branches:
      - develop
      - main
  
  # รันอัตโนมัติเมื่อมี pull request ไปยัง branch develop หรือ main
  pull_request:
    branches:
      - develop
      - main
  
  # รันแบบ Manual (Workflow Dispatch) พร้อม input parameters
  workflow_dispatch:
    inputs:
      action:
        description: 'เลือก Action ที่ต้องการ'
        required: true
        type: choice
        options:
          - 'Build & Deploy'
          - 'Rollback'
        default: 'Build & Deploy'
      rollback_tag:
        description: 'สำหรับ Rollback: ใส่ Image Tag ที่ต้องการ (เช่น Git Hash หรือ dev-123)'
        required: false
        type: string
      rollback_target:
        description: 'สำหรับ Rollback: เลือกว่าจะ Rollback ที่ Environment ไหน'
        required: false
        type: choice
        options:
          - 'dev'
          - 'prod'
        default: 'dev'

# กำหนด Environment Variables ระดับ Workflow
env:
  DOCKER_REPO: iamsamitdev/express-docker-app
  DEV_APP_NAME: express-app-dev
  DEV_HOST_PORT: 3001
  PROD_APP_NAME: express-app-prod
  PROD_HOST_PORT: 3000

# กำหนด Jobs
jobs:
  # =================================================================
  # JOB 1: BUILD & TEST
  # =================================================================
  build-and-test:
    name: Build & Test
    runs-on: ubuntu-latest
    # รันเฉพาะเมื่อเลือก 'Build & Deploy' หรือเป็น push/pull_request
    if: github.event.inputs.action != 'Rollback'
    
    outputs:
      image_tag: ${{ steps.set-tag.outputs.tag }}
    
    steps:
      # Step 1: Checkout code
      - name: Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Set up Node.js
      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '22'
          cache: 'npm'
      
      # Step 3: Install dependencies
      - name: Install dependencies
        run: |
          if [ -f package-lock.json ]; then
            npm ci
          else
            npm install
          fi
      
      # Step 4: Run tests
      - name: Run tests
        run: npm test
      
      # Step 5: Set image tag
      - name: Set image tag
        id: set-tag
        run: |
          if [ "${{ github.ref_name }}" == "main" ]; then
            TAG=$(git rev-parse --short HEAD)
          else
            TAG="dev-${{ github.run_number }}"
          fi
          echo "tag=$TAG" >> $GITHUB_OUTPUT
          echo "Image tag will be: $TAG"
  
  # =================================================================
  # JOB 2: BUILD & PUSH DOCKER IMAGE
  # =================================================================
  build-and-push-docker:
    name: Build & Push Docker Image
    runs-on: ubuntu-latest
    needs: build-and-test
    if: github.event.inputs.action != 'Rollback'
    
    steps:
      # Step 1: Checkout code
      - name: Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Set up Docker Buildx
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      # Step 3: Login to Docker Hub
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      # Step 4: Build and push Docker image
      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          target: production
          push: true
          tags: |
            ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
            ${{ github.ref_name == 'main' && format('{0}:latest', env.DOCKER_REPO) || '' }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
      
      # Step 5: Image digest
      - name: Image digest
        run: echo "Image pushed with tag ${{ needs.build-and-test.outputs.image_tag }}"
  
  # =================================================================
  # JOB 3: DEPLOY TO DEV (เมื่อเป็น branch develop)
  # =================================================================
  deploy-dev:
    name: Deploy to DEV
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker]
    if: github.ref_name == 'develop' && github.event.inputs.action != 'Rollback'
    environment:
      name: development
      url: http://localhost:${{ env.DEV_HOST_PORT }}
    
    steps:
      # Step 1: Deploy to DEV (Local Docker)
      # หมายเหตุ: ในกรณีจริง คุณจะต้องใช้ SSH หรือ Self-hosted runner
      - name: Deploy to DEV environment
        run: |
          echo "Deploying to DEV environment..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Container: ${{ env.DEV_APP_NAME }}"
          echo "Port: ${{ env.DEV_HOST_PORT }}"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
          # docker stop ${{ env.DEV_APP_NAME }} || true
          # docker rm ${{ env.DEV_APP_NAME }} || true
          # docker run -d --name ${{ env.DEV_APP_NAME }} -p ${{ env.DEV_HOST_PORT }}:3000 \
          #   ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
      
      # Step 2: Send notification to n8n
      - name: Send success notification to n8n
        if: success()
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Deploy to DEV\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}\",
              \"container\": \"${{ env.DEV_APP_NAME }}\",
              \"url\": \"http://localhost:${{ env.DEV_HOST_PORT }}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 4: DEPLOY TO PROD (เมื่อเป็น branch main)
  # =================================================================
  # Job 4a: Approval for Production
  approval-prod:
    name: Approval for Production
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker]
    if: github.ref_name == 'main' && github.event.inputs.action != 'Rollback'
    environment:
      name: production-approval
    
    steps:
      - name: Wait for approval
        run: |
          echo "🔐 Waiting for manual approval to deploy to production..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "This step requires approval from designated reviewers"
  
  # Job 4b: Deploy to Production
  deploy-prod:
    name: Deploy to PROD
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker, approval-prod]
    if: github.ref_name == 'main' && github.event.inputs.action != 'Rollback'
    environment:
      name: production
      url: http://localhost:${{ env.PROD_HOST_PORT }}
    
    steps:
      # Step 1: Deploy to PROD (Local Docker)
      - name: Deploy to PROD environment
        run: |
          echo "Deploying to PROD environment..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Container: ${{ env.PROD_APP_NAME }}"
          echo "Port: ${{ env.PROD_HOST_PORT }}"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
          # docker stop ${{ env.PROD_APP_NAME }} || true
          # docker rm ${{ env.PROD_APP_NAME }} || true
          # docker run -d --name ${{ env.PROD_APP_NAME }} -p ${{ env.PROD_HOST_PORT }}:3000 \
          #   ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
      
      # Step 2: Send notification to n8n
      - name: Send success notification to n8n
        if: success()
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Deploy to PROD\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}\",
              \"container\": \"${{ env.PROD_APP_NAME }}\",
              \"url\": \"http://localhost:${{ env.PROD_HOST_PORT }}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 5: ROLLBACK
  # =================================================================
  rollback:
    name: Execute Rollback
    runs-on: ubuntu-latest
    if: github.event.inputs.action == 'Rollback'
    environment:
      name: ${{ github.event.inputs.rollback_target == 'prod' && 'production' || 'development' }}
    
    steps:
      # Step 1: Validate rollback inputs
      - name: Validate rollback inputs
        run: |
          if [ -z "${{ github.event.inputs.rollback_tag }}" ]; then
            echo "Error: ROLLBACK_TAG is required when action is Rollback"
            exit 1
          fi
          echo "Rolling back ${{ github.event.inputs.rollback_target }} to tag: ${{ github.event.inputs.rollback_tag }}"
      
      # Step 2: Execute rollback
      - name: Rollback to previous version
        run: |
          TARGET_ENV="${{ github.event.inputs.rollback_target }}"
          ROLLBACK_TAG="${{ github.event.inputs.rollback_tag }}"
          
          if [ "$TARGET_ENV" == "dev" ]; then
            APP_NAME="${{ env.DEV_APP_NAME }}"
            HOST_PORT="${{ env.DEV_HOST_PORT }}"
          else
            APP_NAME="${{ env.PROD_APP_NAME }}"
            HOST_PORT="${{ env.PROD_HOST_PORT }}"
          fi
          
          IMAGE_TO_DEPLOY="${{ env.DOCKER_REPO }}:${ROLLBACK_TAG}"
          
          echo "Rolling back to: $IMAGE_TO_DEPLOY"
          echo "Target environment: $TARGET_ENV"
          echo "Container name: $APP_NAME"
          echo "Port: $HOST_PORT"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull $IMAGE_TO_DEPLOY
          # docker stop $APP_NAME || true
          # docker rm $APP_NAME || true
          # docker run -d --name $APP_NAME -p $HOST_PORT:3000 $IMAGE_TO_DEPLOY
      
      # Step 3: Send notification to n8n
      - name: Send rollback notification to n8n
        if: success()
        run: |
          TARGET_ENV="${{ github.event.inputs.rollback_target }}"
          if [ "$TARGET_ENV" == "dev" ]; then
            APP_NAME="${{ env.DEV_APP_NAME }}"
            HOST_PORT="${{ env.DEV_HOST_PORT }}"
          else
            APP_NAME="${{ env.PROD_APP_NAME }}"
            HOST_PORT="${{ env.PROD_HOST_PORT }}"
          fi
          
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Rollback ${TARGET_ENV^^}\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ github.event.inputs.rollback_tag }}\",
              \"container\": \"${APP_NAME}\",
              \"url\": \"http://localhost:${HOST_PORT}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 6: NOTIFY ON FAILURE
  # =================================================================
  notify-failure:
    name: Notify on Failure
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker, deploy-dev, deploy-prod, rollback]
    if: failure()
    
    steps:
      - name: Send failure notification to n8n
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Pipeline Failed\",
              \"status\": \"failed\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"N/A\",
              \"container\": \"N/A\",
              \"url\": \"N/A\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
```

---

### 🔐 ขั้นตอนที่ 3: ตั้งค่า GitHub Secrets

**Secrets ที่จำเป็น**:

1. **DOCKERHUB_USERNAME**: ชื่อผู้ใช้ Docker Hub
2. **DOCKERHUB_TOKEN**: Access Token จาก Docker Hub
3. **N8N_WEBHOOK_URL**: URL สำหรับส่ง notification ไปยัง n8n (ถ้ามี)

**วิธีตั้งค่า Secrets**:

1. ไปที่ Repository ใน GitHub
2. คลิก **Settings** → **Secrets and variables** → **Actions**
3. คลิก **New repository secret**
4. เพิ่ม Secrets ทีละตัว:

   ```
   Name: DOCKERHUB_USERNAME
   Secret: your_dockerhub_username
   ```

   ```
   Name: DOCKERHUB_TOKEN
   Secret: your_dockerhub_token
   ```

   ```
   Name: N8N_WEBHOOK_URL
   Secret: https://your-n8n-instance.com/webhook/jenkins
   ```

---

### 🎯 ขั้นตอนที่ 4: สร้าง Docker Hub Access Token

1. ไปที่ [Docker Hub](https://hub.docker.com/)
2. คลิกที่ **Account Settings** → **Security**
3. คลิก **New Access Token**
4. ตั้งชื่อ Token เช่น `github-actions`
5. เลือก Access permissions: **Read, Write, Delete**
6. คลิก **Generate**
7. **คัดลอก Token** (จะแสดงแค่ครั้งเดียว)
8. นำไปใส่ใน GitHub Secret `DOCKERHUB_TOKEN`

---

### 📊 ขั้นตอนที่ 5: ตั้งค่า GitHub Environments และ Approval Mechanism

**สร้าง Environment สำหรับ DEV และ PROD**:

1. ไปที่ Repository → **Settings** → **Environments**
2. คลิก **New environment**
3. สร้าง 3 environments:
   - **development**: สำหรับ DEV
   - **production-approval**: สำหรับ Approval Step
   - **production**: สำหรับ PROD

**ตั้งค่า Protection Rules สำหรับ Production Approval**:

1. เลือก **production-approval** environment
2. เปิดใช้ **Required reviewers** ✅
3. เพิ่ม Reviewers ที่ต้องอนุมัติก่อน deploy (แนะนำอย่างน้อย 2 คน)
4. (Optional) เปิดใช้ **Wait timer** เช่น 5-10 นาที เพื่อให้เวลาตรวจสอบ
5. (Optional) ตั้งค่า **Deployment branches** → Selected branches → `main` เท่านั้น
6. คลิก **Save protection rules**

**ตั้งค่า Protection Rules สำหรับ Production**:

1. เลือก **production** environment
2. สามารถปล่อยไว้ไม่มี protection (เพราะมี approval-prod แล้ว)
3. หรือเพิ่ม **Deployment branches** → Selected branches → `main` เท่านั้น

> **💡 หมายเหตุ**: GitHub Actions ใช้ **Environment Protection Rules** สำหรับ Approval ซึ่งคล้ายกับ `input` ใน Jenkins แต่มีความสามารถมากกว่า เช่น การกำหนด reviewers หลายคน, wait timer, และ audit log ที่ดีกว่า

---

### 🚀 ขั้นตอนที่ 6: Push Code และทดสอบ Workflow

1. **Commit และ Push โค้ด**:
   ```bash
   git add .github/workflows/main.yml
   git commit -m "Add GitHub Actions workflow"
   git push origin develop
   ```

2. **ตรวจสอบ Workflow**:
   - ไปที่ Repository ใน GitHub
   - คลิกแท็บ **Actions**
   - จะเห็น Workflow กำลังรัน

3. **ดูผลลัพธ์**:
   - คลิกที่ Workflow run
   - ดู Logs ของแต่ละ Job

---

### 🔄 ขั้นตอนที่ 7: รัน Workflow และ Approval Process

**7.1 Build & Deploy แบบ Manual**:

1. ไปที่แท็บ **Actions**
2. เลือก Workflow **CI/CD - Express Docker App**
3. คลิก **Run workflow**
4. เลือก:
   - **Branch**: develop หรือ main
   - **Action**: Build & Deploy
5. คลิก **Run workflow**

**7.2 การอนุมัติ Production Deployment** (สำหรับ main branch):

เมื่อ Workflow รันถึง Job **Approval for Production** จะหยุดรอการอนุมัติ:

1. GitHub จะส่ง **Email notification** ให้ Reviewers
2. ไปที่แท็บ **Actions**
3. เลือก Workflow run ที่กำลังรอ (จะมีสถานะ **Waiting**)
4. คลิกปุ่ม **Review deployments** (สีเหลือง)
5. เลือก environment **production-approval**
6. (Optional) ใส่ comment เช่น "Approved for deployment"
7. คลิก **Approve and deploy** (สีเขียว)
   - หรือ **Reject** (สีแดง) ถ้าไม่อนุมัติ

**ผลลัพธ์**:
- ✅ **Approve**: Workflow จะดำเนินการต่อไปยัง Job **Deploy to PROD**
- ❌ **Reject**: Workflow จะ fail และไม่ deploy

**7.3 Rollback แบบ Manual**:

1. ไปที่แท็บ **Actions**
2. เลือก Workflow **CI/CD - Express Docker App**
3. คลิก **Run workflow**
4. เลือก:
   - **Action**: Rollback
   - **rollback_tag**: ใส่ image tag ที่ต้องการ rollback (เช่น `a1b2c3d` หรือ `dev-123`)
   - **rollback_target**: เลือก `dev` หรือ `prod`
5. คลิก **Run workflow**

> **💡 เคล็ดลับ**: สามารถดู Approval history ได้ที่ Repository → Settings → Environments → production-approval → Deployment history

---

### 📸 ขั้นตอนที่ 8: หา Image Tag สำหรับ Rollback

**วิธีหา Image Tag**:

1. **จากหน้า Actions**:
   - ไปที่ Workflow run ที่ต้องการ
   - ดูใน Job "Build & Push Docker Image"
   - ดู Step "Set image tag" จะแสดง tag ที่ใช้

2. **จาก Docker Hub**:
   - ไปที่ [Docker Hub](https://hub.docker.com/)
   - เข้าไปที่ Repository ของคุณ
   - ดูรายการ Tags ที่มีอยู่

3. **จาก Git Commit**:
   - สำหรับ `main` branch: ใช้ Git short hash (7 ตัวแรก)
   ```bash
   git log --oneline
   # ตัวอย่าง: a1b2c3d Add new feature
   ```
   - สำหรับ `develop` branch: ใช้ `dev-{BUILD_NUMBER}`

---

### 🔍 ขั้นตอนที่ 9: ตรวจสอบและ Debug

**9.1 ดู Logs ของ Workflow**:

1. ไปที่แท็บ **Actions**
2. คลิกที่ Workflow run ที่ต้องการดู
3. คลิกที่ Job ที่ต้องการดูรายละเอียด
4. คลิกที่ Step เพื่อดู Logs

**9.2 Debug Mode**:

1. ไปที่ Repository → **Settings** → **Secrets and variables** → **Actions**
2. คลิก **Variables** tab
3. เพิ่ม Variable:
   ```
   Name: ACTIONS_STEP_DEBUG
   Value: true
   ```

4. รัน Workflow ใหม่ จะได้ Logs ละเอียดมากขึ้น

**9.3 ปัญหาที่พบบ่อย**:

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| `Error: Process completed with exit code 1` | Tests ล้มเหลว | ตรวจสอบโค้ดและ tests |
| `Error: buildx failed` | Docker build error | ตรวจสอบ Dockerfile |
| `Error: denied: requested access to the resource is denied` | Docker Hub credentials ผิด | ตรวจสอบ Secrets |
| `Error: Resource not accessible by integration` | ไม่มีสิทธิ์เข้าถึง | ตรวจสอบ Permissions ใน Settings |

---

### 📈 ขั้นตอนที่ 10: เพิ่ม n8n Notification (Optional)

**10.1 สร้าง n8n Webhook**:

1. เปิด n8n Workflow Editor
2. เพิ่ม Node **Webhook**
3. ตั้งค่า:
   - **Method**: POST
   - **Path**: `/webhook/github-actions`
4. คัดลอก **Production URL**

**10.2 เพิ่ม Secret ใน GitHub**:

```
Name: N8N_WEBHOOK_URL
Secret: https://your-n8n-instance.com/webhook/github-actions
```

**10.3 แก้ไข Workflow** (เพิ่ม notification steps):

```yaml
- name: Send notification to n8n
  if: success()
  run: |
    curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
      -H "Content-Type: application/json" \
      -d '{
        "project": "${{ github.repository }}",
        "stage": "Deploy to DEV",
        "status": "success",
        "build": "${{ github.run_number }}",
        "image": "${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
      }'
```

---

### 🎓 ขั้นตอนที่ 11: Best Practices

**11.1 Branch Strategy**:

- **develop**: สำหรับ Development → Deploy to DEV
- **main**: สำหรับ Production → Deploy to PROD
- **feature/***: สำหรับ Feature development → Run tests only

**11.2 Tagging Strategy**:

- **main branch**: ใช้ Git short hash (7 characters)
  - ตัวอย่าง: `a1b2c3d`
- **develop branch**: ใช้ `dev-{BUILD_NUMBER}`
  - ตัวอย่าง: `dev-123`

**11.3 Security**:

- ใช้ **Secrets** สำหรับข้อมูลที่เป็นความลับเสมอ
- อย่า hardcode credentials ในโค้ด
- ใช้ **Environment protection rules** สำหรับ Production

**11.4 Performance**:

- ใช้ **cache** สำหรับ npm dependencies
- ใช้ **Docker layer caching** เพื่อเร่งความเร็ว build
- จำกัด **parallel jobs** ถ้าใช้ Free plan

---

### 📊 ขั้นตอนที่ 12: Monitor และ Analytics

**12.1 ดูสถิติ Workflow**:

1. ไปที่แท็บ **Actions**
2. ดู Workflow runs history
3. ตรวจสอบ:
   - **Success rate**
   - **Average run time**
   - **Failed runs**

**12.2 Insights**:

1. ไปที่ Repository → **Insights** → **Actions**
2. ดูกราฟ:
   - Workflow runs over time
   - Workflow run duration
   - Job execution time

---

### 🔧 ขั้นตอนที่ 13: Deploy จริงด้วย Self-hosted Runner

**สำหรับการ Deploy ไปยัง Server จริง ต้องใช้ Self-hosted Runner**:

**13.1 ติดตั้ง Self-hosted Runner**:

1. ไปที่ Repository → **Settings** → **Actions** → **Runners**
2. คลิก **New self-hosted runner**
3. เลือก OS (Linux/macOS/Windows)
4. ทำตามคำสั่งที่แสดงบนหน้าจอ:

```bash
# Download
mkdir actions-runner && cd actions-runner
curl -o actions-runner-linux-x64-2.311.0.tar.gz -L \
  https://github.com/actions/runner/releases/download/v2.311.0/actions-runner-linux-x64-2.311.0.tar.gz
tar xzf ./actions-runner-linux-x64-2.311.0.tar.gz

# Configure
./config.sh --url https://github.com/YOUR_USERNAME/YOUR_REPO --token YOUR_TOKEN

# Run
./run.sh
```

**13.2 แก้ไข Workflow ให้ใช้ Self-hosted Runner**:

```yaml
deploy-dev:
  name: Deploy to DEV
  runs-on: self-hosted  # เปลี่ยนจาก ubuntu-latest
  needs: [build-and-test, build-and-push-docker]
  if: github.ref_name == 'develop'
  
  steps:
    - name: Deploy to DEV environment
      run: |
        docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
        docker stop ${{ env.DEV_APP_NAME }} || true
        docker rm ${{ env.DEV_APP_NAME }} || true
        docker run -d --name ${{ env.DEV_APP_NAME }} \
          -p ${{ env.DEV_HOST_PORT }}:3000 \
          ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
        docker ps --filter name=${{ env.DEV_APP_NAME }}
```

---

### 📚 สรุป Workflow

**Workflow นี้ประกอบด้วย**:

1. ✅ **Build & Test**: รัน npm test
2. 🐳 **Build Docker Image**: สร้างและ push image ไปยัง Docker Hub
3. 🚀 **Deploy to DEV**: Deploy เมื่อ push ไปยัง `develop` branch
4. 🔐 **Approval for Production**: รอการอนุมัติจาก Reviewers (เฉพาะ `main` branch)
5. 🎯 **Deploy to PROD**: Deploy เมื่อ push ไปยัง `main` branch (หลังจากได้รับการอนุมัติ)
6. 🔄 **Rollback**: Rollback ไปยังเวอร์ชันก่อนหน้า
7. 📢 **Notification**: ส่งการแจ้งเตือนไปยัง n8n (Optional)

**Triggers**:
- ✅ **push** to develop/main
- ✅ **pull_request** to develop/main
- ✅ **workflow_dispatch** (Manual)

**Approval Mechanism**:
- 🔐 ใช้ **Environment Protection Rules** แทน `input` ของ Jenkins
- 👥 รองรับ **Multiple Reviewers** (1-6 คน)
- ⏱️ รองรับ **Wait Timer** (เวลารอก่อน deploy)
- 📧 ส่ง **Email Notification** อัตโนมัติ
- 📊 มี **Audit Log** ครบถ้วน

---

### 🎯 ตัวอย่างการใช้งานจริง

**Scenario 1: Push Feature ไปยัง develop**
```bash
git checkout develop
git add .
git commit -m "Add new feature"
git push origin develop
```
→ Workflow จะรันอัตโนมัติ: Test → Build → Deploy to DEV

**Scenario 2: Merge develop ไปยัง main (Production Deployment)**
```bash
git checkout main
git merge develop
git push origin main
```
→ Workflow จะรันอัตโนมัติ:
1. ✅ Test
2. ✅ Build Docker Image
3. ⏸️ **Approval for Production** (รอการอนุมัติ)
   - GitHub ส่ง email ให้ Reviewers
   - Reviewers ต้องไปอนุมัติที่ Actions tab
4. ✅ Deploy to PROD (หลังจากอนุมัติ)

**Scenario 3: Rollback Production**
1. ไปที่ Actions tab
2. เลือก "CI/CD - Express Docker App"
3. คลิก "Run workflow"
4. ตั้งค่า:
   - Action: Rollback
   - rollback_tag: `a1b2c3d` (git hash ของเวอร์ชันก่อนหน้า)
   - rollback_target: `prod`
5. คลิก "Run workflow"

---

### 📖 ขั้นตอนที่ 14: เอกสารเพิ่มเติม

**สำหรับรายละเอียดเพิ่มเติมเกี่ยวกับ Approval Mechanism**:

ดูไฟล์ **GITHUB_ACTIONS_APPROVAL.md** ที่สร้างไว้ใน `express-docker-app/` ซึ่งมีเนื้อหาครอบคลุม:

- ✅ Step-by-step setup guide สำหรับ Environment และ Protection Rules
- ⚙️ Advanced options (Multiple approvers, Timeout, Custom messages)
- 🎨 Multiple approval levels (QA → Production)
- 📧 Notification setup (Email, Slack, Discord)
- 🔍 Troubleshooting common issues
- 📊 Best practices และ Security guidelines
- 🔄 เปรียบเทียบกับ Jenkins Approval

**ไฟล์ที่เกี่ยวข้อง**:
- `express-docker-app/.github/workflows/main.yml` - Workflow ที่มี Approval
- `express-docker-app/GITHUB_ACTIONS_APPROVAL.md` - คู่มือการตั้งค่า Approval
- `express-docker-app/Jenkinsfile` - เปรียบเทียบกับ Jenkins

---

### Python Flask GitHub Actions

> ตัวอย่าง CI/CD Pipeline สำหรับ Python Flask Application โดยใช้ GitHub Actions พร้อม Docker Build, Deploy, Rollback และ Approval Mechanism

#### 📁 โครงสร้างโปรเจกต์

```
flask-docker-app/
├── .github/
│   └── workflows/
│       └── main.yml          # GitHub Actions Workflow
├── src/
│   └── app.py               # Flask Application
├── tests/
│   └── test_app.py          # Unit Tests (pytest)
├── Dockerfile               # Docker Configuration
├── requirements.txt         # Python Dependencies
└── pytest.ini              # Pytest Configuration
```

---

### 🚀 ขั้นตอนที่ 1: สร้างโครงสร้างโปรเจกต์

1. **สร้าง Directory สำหรับ GitHub Actions Workflow**:
   ```bash
   mkdir -p .github/workflows
   ```

2. **สร้างไฟล์ Workflow**:
   ```bash
   touch .github/workflows/main.yml
   ```

---

### 📝 ขั้นตอนที่ 2: เขียน GitHub Actions Workflow

เปิดไฟล์ `.github/workflows/main.yml` และเขียนโค้ดดังนี้:

```yaml
# ชื่อของ Workflow ที่จะแสดงในหน้า Actions ของ GitHub
name: CI/CD - Flask Docker App

# กำหนด Trigger Events
on:
  # รันอัตโนมัติเมื่อมี push ไปยัง branch develop หรือ main
  push:
    branches:
      - develop
      - main
  
  # รันอัตโนมัติเมื่อมี pull request ไปยัง branch develop หรือ main
  pull_request:
    branches:
      - develop
      - main
  
  # รันแบบ Manual (Workflow Dispatch) พร้อม input parameters
  workflow_dispatch:
    inputs:
      action:
        description: 'เลือก Action ที่ต้องการ'
        required: true
        type: choice
        options:
          - 'Build & Deploy'
          - 'Rollback'
        default: 'Build & Deploy'
      rollback_tag:
        description: 'สำหรับ Rollback: ใส่ Image Tag ที่ต้องการ (เช่น Git Hash หรือ dev-123)'
        required: false
        type: string
      rollback_target:
        description: 'สำหรับ Rollback: เลือกว่าจะ Rollback ที่ Environment ไหน'
        required: false
        type: choice
        options:
          - 'dev'
          - 'prod'
        default: 'dev'

# กำหนด Environment Variables ระดับ Workflow
env:
  DOCKER_REPO: iamsamitdev/flask-docker-app
  DEV_APP_NAME: flask-app-dev
  DEV_HOST_PORT: 5001
  PROD_APP_NAME: flask-app-prod
  PROD_HOST_PORT: 5000

# กำหนด Jobs
jobs:
  # =================================================================
  # JOB 1: BUILD & TEST
  # =================================================================
  build-and-test:
    name: Build & Test
    runs-on: ubuntu-latest
    # รันเฉพาะเมื่อเลือก 'Build & Deploy' หรือเป็น push/pull_request
    if: github.event.inputs.action != 'Rollback'
    
    outputs:
      image_tag: ${{ steps.set-tag.outputs.tag }}
    
    steps:
      # Step 1: Checkout code
      - name: Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Set up Python
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.13'
          cache: 'pip'
      
      # Step 3: Install dependencies
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          if [ -f requirements.txt ]; then
            pip install -r requirements.txt
          fi
      
      # Step 4: Run tests with pytest
      - name: Run tests
        run: |
          pytest -v --tb=short --junitxml=test-results.xml
      
      # Step 5: Upload test results
      - name: Upload test results
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: test-results
          path: test-results.xml
          retention-days: 30
      
      # Step 6: Set image tag
      - name: Set image tag
        id: set-tag
        run: |
          if [ "${{ github.ref_name }}" == "main" ]; then
            TAG=$(git rev-parse --short HEAD)
          else
            TAG="dev-${{ github.run_number }}"
          fi
          echo "tag=$TAG" >> $GITHUB_OUTPUT
          echo "Image tag will be: $TAG"
  
  # =================================================================
  # JOB 2: BUILD & PUSH DOCKER IMAGE
  # =================================================================
  build-and-push-docker:
    name: Build & Push Docker Image
    runs-on: ubuntu-latest
    needs: build-and-test
    if: github.event.inputs.action != 'Rollback'
    
    steps:
      # Step 1: Checkout code
      - name: Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Set up Docker Buildx
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      # Step 3: Login to Docker Hub
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      # Step 4: Build and push Docker image
      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: |
            ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
            ${{ github.ref_name == 'main' && format('{0}:latest', env.DOCKER_REPO) || '' }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
      
      # Step 5: Image digest
      - name: Image digest
        run: echo "Image pushed with tag ${{ needs.build-and-test.outputs.image_tag }}"
  
  # =================================================================
  # JOB 3: DEPLOY TO DEV (เมื่อเป็น branch develop)
  # =================================================================
  deploy-dev:
    name: Deploy to DEV
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker]
    if: github.ref_name == 'develop' && github.event.inputs.action != 'Rollback'
    environment:
      name: development
      url: http://localhost:${{ env.DEV_HOST_PORT }}
    
    steps:
      # Step 1: Deploy to DEV (Local Docker)
      # หมายเหตุ: ในกรณีจริง คุณจะต้องใช้ SSH หรือ Self-hosted runner
      - name: Deploy to DEV environment
        run: |
          echo "Deploying to DEV environment..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Container: ${{ env.DEV_APP_NAME }}"
          echo "Port: ${{ env.DEV_HOST_PORT }}"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
          # docker stop ${{ env.DEV_APP_NAME }} || true
          # docker rm ${{ env.DEV_APP_NAME }} || true
          # docker run -d --name ${{ env.DEV_APP_NAME }} -p ${{ env.DEV_HOST_PORT }}:5000 \
          #   ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
      
      # Step 2: Send notification to n8n
      - name: Send success notification to n8n
        if: success()
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Deploy to DEV\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}\",
              \"container\": \"${{ env.DEV_APP_NAME }}\",
              \"url\": \"http://localhost:${{ env.DEV_HOST_PORT }}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 4: APPROVAL FOR PRODUCTION
  # =================================================================
  approval-prod:
    name: Approval for Production
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker]
    if: github.ref_name == 'main' && github.event.inputs.action != 'Rollback'
    environment:
      name: production-approval
    
    steps:
      - name: Wait for approval
        run: |
          echo "🔐 Production Deployment Approval Required!"
          echo "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━"
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Build: #${{ github.run_number }}"
          echo "Commit: ${{ github.sha }}"
          echo "Author: ${{ github.actor }}"
          echo "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━"
          echo "Waiting for manual approval..."
  
  # =================================================================
  # JOB 5: DEPLOY TO PROD (เมื่อเป็น branch main)
  # =================================================================
  deploy-prod:
    name: Deploy to PROD
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker, approval-prod]
    if: github.ref_name == 'main' && github.event.inputs.action != 'Rollback'
    environment:
      name: production
      url: http://localhost:${{ env.PROD_HOST_PORT }}
    
    steps:
      # Step 1: Deploy to PROD (Local Docker)
      - name: Deploy to PROD environment
        run: |
          echo "Deploying to PROD environment..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Container: ${{ env.PROD_APP_NAME }}"
          echo "Port: ${{ env.PROD_HOST_PORT }}"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
          # docker stop ${{ env.PROD_APP_NAME }} || true
          # docker rm ${{ env.PROD_APP_NAME }} || true
          # docker run -d --name ${{ env.PROD_APP_NAME }} -p ${{ env.PROD_HOST_PORT }}:5000 \
          #   ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
      
      # Step 2: Send notification to n8n
      - name: Send success notification to n8n
        if: success()
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Deploy to PROD\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}\",
              \"container\": \"${{ env.PROD_APP_NAME }}\",
              \"url\": \"http://localhost:${{ env.PROD_HOST_PORT }}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 6: ROLLBACK
  # =================================================================
  rollback:
    name: Execute Rollback
    runs-on: ubuntu-latest
    if: github.event.inputs.action == 'Rollback'
    environment:
      name: ${{ github.event.inputs.rollback_target == 'prod' && 'production' || 'development' }}
    
    steps:
      # Step 1: Validate rollback inputs
      - name: Validate rollback inputs
        run: |
          if [ -z "${{ github.event.inputs.rollback_tag }}" ]; then
            echo "Error: ROLLBACK_TAG is required when action is Rollback"
            exit 1
          fi
          echo "Rolling back ${{ github.event.inputs.rollback_target }} to tag: ${{ github.event.inputs.rollback_tag }}"
      
      # Step 2: Execute rollback
      - name: Rollback to previous version
        run: |
          TARGET_ENV="${{ github.event.inputs.rollback_target }}"
          ROLLBACK_TAG="${{ github.event.inputs.rollback_tag }}"
          
          if [ "$TARGET_ENV" == "dev" ]; then
            APP_NAME="${{ env.DEV_APP_NAME }}"
            HOST_PORT="${{ env.DEV_HOST_PORT }}"
          else
            APP_NAME="${{ env.PROD_APP_NAME }}"
            HOST_PORT="${{ env.PROD_HOST_PORT }}"
          fi
          
          IMAGE_TO_DEPLOY="${{ env.DOCKER_REPO }}:${ROLLBACK_TAG}"
          
          echo "Rolling back to: $IMAGE_TO_DEPLOY"
          echo "Target environment: $TARGET_ENV"
          echo "Container name: $APP_NAME"
          echo "Port: $HOST_PORT"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull $IMAGE_TO_DEPLOY
          # docker stop $APP_NAME || true
          # docker rm $APP_NAME || true
          # docker run -d --name $APP_NAME -p $HOST_PORT:5000 $IMAGE_TO_DEPLOY
      
      # Step 3: Send notification to n8n
      - name: Send rollback notification to n8n
        if: success()
        run: |
          TARGET_ENV="${{ github.event.inputs.rollback_target }}"
          if [ "$TARGET_ENV" == "dev" ]; then
            APP_NAME="${{ env.DEV_APP_NAME }}"
            HOST_PORT="${{ env.DEV_HOST_PORT }}"
          else
            APP_NAME="${{ env.PROD_APP_NAME }}"
            HOST_PORT="${{ env.PROD_HOST_PORT }}"
          fi
          
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Rollback ${TARGET_ENV^^}\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ github.event.inputs.rollback_tag }}\",
              \"container\": \"${APP_NAME}\",
              \"url\": \"http://localhost:${HOST_PORT}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 7: NOTIFY ON FAILURE
  # =================================================================
  notify-failure:
    name: Notify on Failure
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker, deploy-dev, deploy-prod, rollback]
    if: failure()
    
    steps:
      - name: Send failure notification to n8n
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Pipeline Failed\",
              \"status\": \"failed\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"N/A\",
              \"container\": \"N/A\",
              \"url\": \"N/A\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"

```
---

### 🔐 ขั้นตอนที่ 3: ตั้งค่า GitHub Secrets

**Secrets ที่จำเป็น** (เหมือน Express):

1. **DOCKERHUB_USERNAME**: ชื่อผู้ใช้ Docker Hub
2. **DOCKERHUB_TOKEN**: Access Token จาก Docker Hub
3. **N8N_WEBHOOK_URL**: URL สำหรับส่ง notification ไปยัง n8n (ถ้ามี)

**วิธีตั้งค่า Secrets**:

1. ไปที่ Repository ใน GitHub
2. คลิก **Settings** → **Secrets and variables** → **Actions**
3. คลิก **New repository secret**
4. เพิ่ม Secrets ทีละตัว (ใช้ค่าเดียวกับที่ตั้งไว้สำหรับ Express)

---

### 🎯 ขั้นตอนที่ 4: สร้าง Docker Hub Access Token

> ใช้ Token เดียวกับที่สร้างไว้สำหรับ Express ได้เลย หรือสร้างใหม่ก็ได้

ถ้ายังไม่มี ให้ทำตามขั้นตอน:

1. ไปที่ [Docker Hub](https://hub.docker.com/)
2. คลิกที่ **Account Settings** → **Security**
3. คลิก **New Access Token**
4. ตั้งชื่อ Token เช่น `github-actions-flask`
5. เลือก Access permissions: **Read, Write, Delete**
6. คลิก **Generate**
7. **คัดลอก Token** (จะแสดงแค่ครั้งเดียว)
8. นำไปใส่ใน GitHub Secret `DOCKERHUB_TOKEN`

---

### 📊 ขั้นตอนที่ 5: ตั้งค่า GitHub Environments และ Approval Mechanism

**สร้าง Environment สำหรับ DEV และ PROD**:

1. ไปที่ Repository → **Settings** → **Environments**
2. คลิก **New environment**
3. สร้าง 3 environments:
   - **development**: สำหรับ DEV
   - **production-approval**: สำหรับ Approval Step
   - **production**: สำหรับ PROD

**ตั้งค่า Protection Rules สำหรับ Production Approval**:

1. เลือก **production-approval** environment
2. เปิดใช้ **Required reviewers** ✅
3. เพิ่ม Reviewers ที่ต้องอนุมัติก่อน deploy (แนะนำอย่างน้อย 2 คน)
4. (Optional) เปิดใช้ **Wait timer** เช่น 5-10 นาที
5. (Optional) ตั้งค่า **Deployment branches** → Selected branches → `main` เท่านั้น
6. คลิก **Save protection rules**

> **💡 หมายเหตุ**: Flask ใช้ Approval Mechanism เหมือนกับ Express ทุกประการ

---

### 🚀 ขั้นตอนที่ 6: Push Code และทดสอบ Workflow

1. **Commit และ Push โค้ด**:
   ```bash
   git add .github/workflows/main.yml
   git commit -m "Add GitHub Actions workflow for Flask"
   git push origin develop
   ```

2. **ตรวจสอบ Workflow**:
   - ไปที่ Repository ใน GitHub
   - คลิกแท็บ **Actions**
   - จะเห็น Workflow กำลังรัน

3. **ดูผลลัพธ์**:
   - คลิกที่ Workflow run
   - ดู Logs ของแต่ละ Job
   - ตรวจสอบว่า pytest tests ผ่านหรือไม่

---

### 🔄 ขั้นตอนที่ 7: รัน Workflow และ Approval Process

**7.1 Build & Deploy แบบ Manual**:

1. ไปที่แท็บ **Actions**
2. เลือก Workflow **CI/CD - Flask Docker App**
3. คลิก **Run workflow**
4. เลือก:
   - **Branch**: develop หรือ main
   - **Action**: Build & Deploy
5. คลิก **Run workflow**

**7.2 การอนุมัติ Production Deployment** (สำหรับ main branch):

เมื่อ Workflow รันถึง Job **Approval for Production** จะหยุดรอการอนุมัติ:

1. GitHub จะส่ง **Email notification** ให้ Reviewers
2. ไปที่แท็บ **Actions**
3. เลือก Workflow run ที่กำลังรอ (จะมีสถานะ **Waiting**)
4. คลิกปุ่ม **Review deployments** (สีเหลือง)
5. เลือก environment **production-approval**
6. (Optional) ใส่ comment เช่น "Approved for Flask production deployment"
7. คลิก **Approve and deploy** (สีเขียว)
   - หรือ **Reject** (สีแดง) ถ้าไม่อนุมัติ

**ผลลัพธ์**:
- ✅ **Approve**: Workflow จะดำเนินการต่อไปยัง Job **Deploy to PROD**
- ❌ **Reject**: Workflow จะ fail และไม่ deploy

**7.3 Rollback แบบ Manual**:

1. ไปที่แท็บ **Actions**
2. เลือก Workflow **CI/CD - Flask Docker App**
3. คลิก **Run workflow**
4. เลือก:
   - **Action**: Rollback
   - **rollback_tag**: ใส่ image tag (เช่น `a1b2c3d` หรือ `dev-123`)
   - **rollback_target**: เลือก `dev` หรือ `prod`
5. คลิก **Run workflow**

---

### 📸 ขั้นตอนที่ 8: หา Image Tag สำหรับ Rollback

**วิธีหา Image Tag** (เหมือน Express):

1. **จากหน้า Actions**:
   - ไปที่ Workflow run ที่ต้องการ
   - ดูใน Job "Build & Push Docker Image"
   - ดู Step "Set image tag" จะแสดง tag ที่ใช้

2. **จาก Docker Hub**:
   - ไปที่ [Docker Hub](https://hub.docker.com/)
   - เข้าไปที่ Repository `iamsamitdev/flask-docker-app`
   - ดูรายการ Tags ที่มีอยู่

3. **จาก Git Commit**:
   - สำหรับ `main` branch: ใช้ Git short hash (7 ตัวแรก)
   ```bash
   git log --oneline
   # ตัวอย่าง: a1b2c3d Add new feature
   ```
   - สำหรับ `develop` branch: ใช้ `dev-{BUILD_NUMBER}`

---

### 🔍 ขั้นตอนที่ 9: ตรวจสอบและ Debug

**9.1 ดู Logs ของ Workflow**:

1. ไปที่แท็บ **Actions**
2. คลิกที่ Workflow run ที่ต้องการดู
3. คลิกที่ Job ที่ต้องการดูรายละเอียด
4. คลิกที่ Step เพื่อดู Logs

**9.2 Debug Mode**:

1. ไปที่ Repository → **Settings** → **Secrets and variables** → **Actions**
2. คลิก **Variables** tab
3. เพิ่ม Variable:
   ```
   Name: ACTIONS_STEP_DEBUG
   Value: true
   ```

4. รัน Workflow ใหม่ จะได้ Logs ละเอียดมากขึ้น

**9.3 ปัญหาที่พบบ่อยสำหรับ Flask**:

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| `Error: Process completed with exit code 1` | pytest tests ล้มเหลว | ตรวจสอบโค้ดและ tests |
| `ModuleNotFoundError: No module named 'flask'` | ไม่ได้ติดตั้ง dependencies | ตรวจสอบ requirements.txt |
| `Error: buildx failed` | Docker build error | ตรวจสอบ Dockerfile |
| `Error: denied: requested access to the resource is denied` | Docker Hub credentials ผิด | ตรวจสอบ Secrets |
| `pytest: not found` | pytest ไม่ได้ติดตั้ง | เพิ่ม pytest ใน requirements.txt |
| `Port 5000 already in use` | Port conflict | เปลี่ยน port หรือหยุด container เดิม |

---

### 📈 ขั้นตอนที่ 10: เพิ่ม n8n Notification

**10.1 สร้าง n8n Webhook**:

1. เปิด n8n Workflow Editor
2. เพิ่ม Node **Webhook**
3. ตั้งค่า:
   - **Method**: POST
   - **Path**: `/webhook/flask-actions` (หรือใช้ path เดียวกับ Express)
4. คัดลอก **Production URL**

**10.2 เพิ่ม Secret ใน GitHub**:

```
Name: N8N_WEBHOOK_URL
Secret: https://your-n8n-instance.com/webhook/flask-actions
```

> **💡 Note**: สามารถใช้ webhook URL เดียวกับ Express ได้ (แยกด้วย field `project`)

**10.3 Notification ถูกเพิ่มไว้ใน Workflow แล้ว**:

- ✅ Deploy to DEV success
- ✅ Deploy to PROD success
- ✅ Rollback success
- ✅ Pipeline failure

---

### 🎓 ขั้นตอนที่ 11: Best Practices สำหรับ Flask

**11.1 Branch Strategy** (เหมือน Express):

- **develop**: สำหรับ Development → Deploy to DEV (port 5001)
- **main**: สำหรับ Production → Deploy to PROD (port 5000)
- **feature/***: สำหรับ Feature development → Run tests only

**11.2 Tagging Strategy** (เหมือน Express):

- **main branch**: ใช้ Git short hash (7 characters)
  - ตัวอย่าง: `a1b2c3d`
- **develop branch**: ใช้ `dev-{BUILD_NUMBER}`
  - ตัวอย่าง: `dev-123`

**11.3 Testing Strategy**:

- ใช้ **pytest** สำหรับ unit tests
- ใช้ **pytest-cov** สำหรับ code coverage
- เพิ่ม **pytest.ini** สำหรับ configuration
- ใช้ **--junitxml** เพื่อ export test results

**11.4 Security**:

- ใช้ **Secrets** สำหรับข้อมูลที่เป็นความลับเสมอ
- อย่า hardcode API keys หรือ passwords ในโค้ด
- ใช้ **Environment protection rules** สำหรับ Production
- ใช้ **.gitignore** สำหรับไฟล์ที่ไม่ควร commit (*.pyc, __pycache__, .env)

**11.5 Performance**:

- ใช้ **cache: 'pip'** สำหรับ pip dependencies
- ใช้ **Docker layer caching** เพื่อเร่งความเร็ว build
- ใช้ **python:3.13-slim** แทน python:3.13 เพื่อลดขนาด image

---

### 📊 ขั้นตอนที่ 12: Monitor และ Analytics

**12.1 ดูสถิติ Workflow**:

1. ไปที่แท็บ **Actions**
2. ดู Workflow runs history
3. ตรวจสอบ:
   - **Success rate**
   - **Average run time**
   - **Failed runs**

**12.2 Test Results**:

1. เข้าไปดู Workflow run
2. ดู **Summary** tab
3. จะเห็น test results ที่ upload มา
4. คลิกดูรายละเอียด tests ที่ผ่านและไม่ผ่าน

---

### 🔧 ขั้นตอนที่ 13: Deploy จริงด้วย Self-hosted Runner

**สำหรับการ Deploy ไปยัง Server จริง ต้องใช้ Self-hosted Runner**:

**13.1 ติดตั้ง Self-hosted Runner** (เหมือน Express):

1. ไปที่ Repository → **Settings** → **Actions** → **Runners**
2. คลิก **New self-hosted runner**
3. เลือก OS (Linux/macOS/Windows)
4. ทำตามคำสั่งที่แสดงบนหน้าจอ

**13.2 แก้ไข Workflow ให้ใช้ Self-hosted Runner**:

```yaml
deploy-dev:
  name: Deploy to DEV
  runs-on: self-hosted  # เปลี่ยนจาก ubuntu-latest
  needs: [build-and-test, build-and-push-docker]
  if: github.ref_name == 'develop'
  
  steps:
    - name: Deploy to DEV environment
      run: |
        docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
        docker stop ${{ env.DEV_APP_NAME }} || true
        docker rm ${{ env.DEV_APP_NAME }} || true
        docker run -d --name ${{ env.DEV_APP_NAME }} \
          -p ${{ env.DEV_HOST_PORT }}:5000 \
          ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
        docker ps --filter name=${{ env.DEV_APP_NAME }}
```

---

### 📚 สรุป Workflow

**Workflow นี้ประกอบด้วย**:

1. ✅ **Build & Test**: รัน pytest tests
2. 🐳 **Build Docker Image**: สร้างและ push image ไปยัง Docker Hub
3. 🚀 **Deploy to DEV**: Deploy เมื่อ push ไปยัง `develop` branch (port 5001)
4. 🔐 **Approval for Production**: รอการอนุมัติจาก Reviewers (เฉพาะ `main` branch)
5. 🎯 **Deploy to PROD**: Deploy เมื่อ push ไปยัง `main` branch (port 5000, หลังจากได้รับการอนุมัติ)
6. 🔄 **Rollback**: Rollback ไปยังเวอร์ชันก่อนหน้า
7. 📢 **Notification**: ส่งการแจ้งเตือนไปยัง n8n

**Triggers**:
- ✅ **push** to develop/main
- ✅ **pull_request** to develop/main
- ✅ **workflow_dispatch** (Manual)

**Approval Mechanism**:
- 🔐 ใช้ **Environment Protection Rules** แทน `input` ของ Jenkins
- 👥 รองรับ **Multiple Reviewers** (1-6 คน)
- ⏱️ รองรับ **Wait Timer** (เวลารอก่อน deploy)
- 📧 ส่ง **Email Notification** อัตโนมัติ
- 📊 มี **Audit Log** ครบถ้วน

---

### 🎯 ตัวอย่างการใช้งานจริง

**Scenario 1: Push Feature ไปยัง develop**
```bash
git checkout develop
git add .
git commit -m "Add new Flask endpoint"
git push origin develop
```
→ Workflow จะรันอัตโนมัติ: pytest → Build → Deploy to DEV (port 5001)

**Scenario 2: Merge develop ไปยัง main (Production Deployment)**
```bash
git checkout main
git merge develop
git push origin main
```
→ Workflow จะรันอัตโนมัติ:
1. ✅ pytest tests
2. ✅ Build Docker Image
3. ⏸️ **Approval for Production** (รอการอนุมัติ)
   - GitHub ส่ง email ให้ Reviewers
   - Reviewers ต้องไปอนุมัติที่ Actions tab
4. ✅ Deploy to PROD (port 5000, หลังจากอนุมัติ)

**Scenario 3: Rollback Production**
1. ไปที่ Actions tab
2. เลือก "CI/CD - Flask Docker App"
3. คลิก "Run workflow"
4. ตั้งค่า:
   - Action: Rollback
   - rollback_tag: `a1b2c3d` (git hash ของเวอร์ชันก่อนหน้า)
   - rollback_target: `prod`
5. คลิก "Run workflow"

---

### 📖 ขั้นตอนที่ 14: เอกสารเพิ่มเติม

**สำหรับรายละเอียดเพิ่มเติมเกี่ยวกับ Approval Mechanism**:

ดูไฟล์ **GITHUB_ACTIONS_APPROVAL.md** ที่สร้างไว้ใน `express-docker-app/` ซึ่งใช้ได้กับ Flask เช่นกัน:

- ✅ Step-by-step setup guide สำหรับ Environment และ Protection Rules
- ⚙️ Advanced options (Multiple approvers, Timeout, Custom messages)
- 🎨 Multiple approval levels (QA → Production)
- 📧 Notification setup (Email, Slack, Discord)
- 🔍 Troubleshooting common issues
- 📊 Best practices และ Security guidelines
- 🔄 เปรียบเทียบกับ Jenkins Approval

**ไฟล์ที่เกี่ยวข้อง**:
- `flask-docker-app/.github/workflows/main.yml` - Workflow สำหรับ Flask
- `flask-docker-app/Jenkinsfile` - เปรียบเทียบกับ Jenkins
- `express-docker-app/GITHUB_ACTIONS_APPROVAL.md` - คู่มือการตั้งค่า Approval (ใช้ได้ทั้ง Express และ Flask)

---

### 🔄 เปรียบเทียบ GitHub Actions vs Jenkins สำหรับ Flask

| Feature | Jenkins (Jenkinsfile) | GitHub Actions (main.yml) |
|---------|----------------------|---------------------------|
| **Syntax** | Groovy DSL | YAML |
| **Setup Location** | Jenkinsfile | .github/workflows/main.yml |
| **Agent/Runner** | `agent any` | `runs-on: ubuntu-latest` |
| **Python Setup** | `docker.image('python:3.13-slim').inside` | `actions/setup-python@v5` |
| **Install Deps** | `pip install -r requirements.txt` | `pip install -r requirements.txt` |
| **Tests** | `pytest -v --junitxml=test-results.xml` | `pytest -v --junitxml=test-results.xml` |
| **Docker Build** | `docker.build()` | `docker/build-push-action@v5` |
| **Docker Push** | `customImage.push()` | Built-in to build-push-action |
| **Approval** | `input message: "Deploy?"` | `environment: production-approval` |
| **Rollback** | Parameters + stages | workflow_dispatch inputs |
| **Notification** | Custom function + HTTP Request | curl to n8n webhook |
| **Secrets** | Jenkins Credentials | GitHub Secrets |
| **Environment** | Environment variables | env: block |
| **Conditional** | `when { expression }` | `if:` condition |

---

### Java Spring Boot GitHub Actions

> ตัวอย่าง CI/CD Pipeline สำหรับ Java Spring Boot Application โดยใช้ GitHub Actions พร้อม Maven Build, Docker Build, Deploy, Rollback และ Approval Mechanism

#### 📁 โครงสร้างโปรเจกต์

```
springboot-docker-app/
├── .github/
│   └── workflows/
│       └── main.yml          # GitHub Actions Workflow
├── src/
│   ├── main/
│   │   └── java/            # Spring Boot Application
│   └── test/
│       └── java/            # Unit Tests (JUnit)
├── Dockerfile               # Docker Configuration
├── pom.xml                  # Maven Dependencies
└── target/                  # Build Output (Auto-generated)
    └── *.jar               # Spring Boot JAR
```

---

### 🚀 ขั้นตอนที่ 1: สร้างโครงสร้างโปรเจกต์

1. **สร้าง Directory สำหรับ GitHub Actions Workflow**:
   ```bash
   mkdir -p .github/workflows
   ```

2. **สร้างไฟล์ Workflow**:
   ```bash
   touch .github/workflows/main.yml
   ```

---

### 📝 ขั้นตอนที่ 2: เขียน GitHub Actions Workflow

เปิดไฟล์ `.github/workflows/main.yml` และเขียนโค้ดดังนี้:

```yaml
# ชื่อของ Workflow ที่จะแสดงในหน้า Actions ของ GitHub
name: CI/CD - Spring Boot Docker App

# กำหนด Trigger Events
on:
  # รันอัตโนมัติเมื่อมี push ไปยัง branch develop หรือ main
  push:
    branches:
      - develop
      - main
  
  # รันอัตโนมัติเมื่อมี pull request ไปยัง branch develop หรือ main
  pull_request:
    branches:
      - develop
      - main
  
  # รันแบบ Manual (Workflow Dispatch) พร้อม input parameters
  workflow_dispatch:
    inputs:
      action:
        description: 'เลือก Action ที่ต้องการ'
        required: true
        type: choice
        options:
          - 'Build & Deploy'
          - 'Rollback'
        default: 'Build & Deploy'
      rollback_tag:
        description: 'สำหรับ Rollback: ใส่ Image Tag ที่ต้องการ (เช่น Git Hash หรือ dev-123)'
        required: false
        type: string
      rollback_target:
        description: 'สำหรับ Rollback: เลือกว่าจะ Rollback ที่ Environment ไหน'
        required: false
        type: choice
        options:
          - 'dev'
          - 'prod'
        default: 'dev'
      project_dir_override:
        description: 'ทางเลือก: ระบุโฟลเดอร์โปรเจกต์ที่มี pom.xml (ปล่อยว่างให้ระบบค้นหาอัตโนมัติ)'
        required: false
        type: string

# กำหนด Environment Variables ระดับ Workflow
env:
  DOCKER_REPO: iamsamitdev/springboot-docker-app
  DEV_APP_NAME: springboot-app-dev
  DEV_HOST_PORT: 8081
  PROD_APP_NAME: springboot-app-prod
  PROD_HOST_PORT: 8080

# กำหนด Jobs
jobs:
  # =================================================================
  # JOB 1: BUILD & TEST
  # =================================================================
  build-and-test:
    name: Build & Test
    runs-on: ubuntu-latest
    # รันเฉพาะเมื่อเลือก 'Build & Deploy' หรือเป็น push/pull_request
    if: github.event.inputs.action != 'Rollback'
    
    outputs:
      image_tag: ${{ steps.set-tag.outputs.tag }}
      project_dir: ${{ steps.find-project.outputs.dir }}
    
    steps:
      # Step 1: Checkout code
      - name: Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Find project directory with pom.xml
      - name: Find project directory
        id: find-project
        run: |
          if [ -n "${{ github.event.inputs.project_dir_override }}" ]; then
            PROJECT_DIR="${{ github.event.inputs.project_dir_override }}"
          else
            # ค้นหา pom.xml อัตโนมัติ
            POM_FILE=$(find . -name "pom.xml" -type f | head -1)
            if [ -z "$POM_FILE" ]; then
              echo "Error: ไม่พบ pom.xml ใน workspace"
              exit 1
            fi
            PROJECT_DIR=$(dirname "$POM_FILE")
            # ถ้า pom.xml อยู่ที่ root ให้ใช้ current directory
            if [ "$PROJECT_DIR" = "." ]; then
              PROJECT_DIR="."
            fi
          fi
          echo "dir=$PROJECT_DIR" >> $GITHUB_OUTPUT
          echo "Project directory: $PROJECT_DIR"
      
      # Step 3: Set up Java
      - name: Set up Java
        uses: actions/setup-java@v4
        with:
          java-version: '21'
          distribution: 'temurin'
          cache: 'maven'
      
      # Step 4: Run tests and package
      - name: Run Maven Test & Package
        working-directory: ${{ steps.find-project.outputs.dir }}
        run: |
          echo "Running Maven Test & Package..."
          mvn -B -ntp clean package
      
      # Step 5: Upload test results
      - name: Upload test results
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: test-results
          path: ${{ steps.find-project.outputs.dir }}/target/surefire-reports/*.xml
          retention-days: 30
      
      # Step 6: Upload JAR artifact
      - name: Upload JAR artifact
        uses: actions/upload-artifact@v4
        with:
          name: spring-boot-jar
          path: ${{ steps.find-project.outputs.dir }}/target/*.jar
          retention-days: 30
      
      # Step 7: Set image tag
      - name: Set image tag
        id: set-tag
        run: |
          if [ "${{ github.ref_name }}" == "main" ]; then
            TAG=$(git rev-parse --short HEAD)
          else
            TAG="dev-${{ github.run_number }}"
          fi
          echo "tag=$TAG" >> $GITHUB_OUTPUT
          echo "Image tag will be: $TAG"
  
  # =================================================================
  # JOB 2: BUILD & PUSH DOCKER IMAGE
  # =================================================================
  build-and-push-docker:
    name: Build & Push Docker Image
    runs-on: ubuntu-latest
    needs: build-and-test
    if: github.event.inputs.action != 'Rollback'
    
    steps:
      # Step 1: Checkout code
      - name: Checkout code
        uses: actions/checkout@v4
      
      # Step 2: Download JAR artifact
      - name: Download JAR artifact
        uses: actions/download-artifact@v4
        with:
          name: spring-boot-jar
          path: ${{ needs.build-and-test.outputs.project_dir }}/target/
      
      # Step 3: Set up Docker Buildx
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      # Step 4: Login to Docker Hub
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      # Step 5: Build and push Docker image
      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: ${{ needs.build-and-test.outputs.project_dir }}
          push: true
          tags: |
            ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
            ${{ github.ref_name == 'main' && format('{0}:latest', env.DOCKER_REPO) || '' }}
          cache-from: type=gha
          cache-to: type=gha,mode=max
      
      # Step 6: Image digest
      - name: Image digest
        run: echo "Image pushed with tag ${{ needs.build-and-test.outputs.image_tag }}"
  
  # =================================================================
  # JOB 3: DEPLOY TO DEV (เมื่อเป็น branch develop)
  # =================================================================
  deploy-dev:
    name: Deploy to DEV
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker]
    if: github.ref_name == 'develop' && github.event.inputs.action != 'Rollback'
    environment:
      name: development
      url: http://localhost:${{ env.DEV_HOST_PORT }}
    
    steps:
      # Step 1: Deploy to DEV (Local Docker)
      # หมายเหตุ: ในกรณีจริง คุณจะต้องใช้ SSH หรือ Self-hosted runner
      - name: Deploy to DEV environment
        run: |
          echo "Deploying to DEV environment..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Container: ${{ env.DEV_APP_NAME }}"
          echo "Port: ${{ env.DEV_HOST_PORT }}"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
          # docker stop ${{ env.DEV_APP_NAME }} || true
          # docker rm ${{ env.DEV_APP_NAME }} || true
          # docker run -d --name ${{ env.DEV_APP_NAME }} -p ${{ env.DEV_HOST_PORT }}:8080 \
          #   ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
      
      # Step 2: Send notification to n8n
      - name: Send success notification to n8n
        if: success()
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Deploy to DEV\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}\",
              \"container\": \"${{ env.DEV_APP_NAME }}\",
              \"url\": \"http://localhost:${{ env.DEV_HOST_PORT }}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 4: APPROVAL FOR PRODUCTION
  # =================================================================
  approval-prod:
    name: Approval for Production
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker]
    if: github.ref_name == 'main' && github.event.inputs.action != 'Rollback'
    environment:
      name: production-approval
    
    steps:
      - name: Wait for approval
        run: |
          echo "🔐 Production Deployment Approval Required!"
          echo "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━"
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Build: #${{ github.run_number }}"
          echo "Commit: ${{ github.sha }}"
          echo "Author: ${{ github.actor }}"
          echo "Project: Spring Boot Application"
          echo "Port: ${{ env.PROD_HOST_PORT }}"
          echo "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━"
          echo "Waiting for manual approval..."
  
  # =================================================================
  # JOB 5: DEPLOY TO PROD (เมื่อเป็น branch main)
  # =================================================================
  deploy-prod:
    name: Deploy to PROD
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker, approval-prod]
    if: github.ref_name == 'main' && github.event.inputs.action != 'Rollback'
    environment:
      name: production
      url: http://localhost:${{ env.PROD_HOST_PORT }}
    
    steps:
      # Step 1: Deploy to PROD (Local Docker)
      - name: Deploy to PROD environment
        run: |
          echo "Deploying to PROD environment..."
          echo "Image: ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}"
          echo "Container: ${{ env.PROD_APP_NAME }}"
          echo "Port: ${{ env.PROD_HOST_PORT }}"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
          # docker stop ${{ env.PROD_APP_NAME }} || true
          # docker rm ${{ env.PROD_APP_NAME }} || true
          # docker run -d --name ${{ env.PROD_APP_NAME }} -p ${{ env.PROD_HOST_PORT }}:8080 \
          #   ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
      
      # Step 2: Send notification to n8n
      - name: Send success notification to n8n
        if: success()
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Deploy to PROD\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}\",
              \"container\": \"${{ env.PROD_APP_NAME }}\",
              \"url\": \"http://localhost:${{ env.PROD_HOST_PORT }}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 6: ROLLBACK
  # =================================================================
  rollback:
    name: Execute Rollback
    runs-on: ubuntu-latest
    if: github.event.inputs.action == 'Rollback'
    environment:
      name: ${{ github.event.inputs.rollback_target == 'prod' && 'production' || 'development' }}
    
    steps:
      # Step 1: Validate rollback inputs
      - name: Validate rollback inputs
        run: |
          if [ -z "${{ github.event.inputs.rollback_tag }}" ]; then
            echo "Error: ROLLBACK_TAG is required when action is Rollback"
            exit 1
          fi
          echo "Rolling back ${{ github.event.inputs.rollback_target }} to tag: ${{ github.event.inputs.rollback_tag }}"
      
      # Step 2: Execute rollback
      - name: Rollback to previous version
        run: |
          TARGET_ENV="${{ github.event.inputs.rollback_target }}"
          ROLLBACK_TAG="${{ github.event.inputs.rollback_tag }}"
          
          if [ "$TARGET_ENV" == "dev" ]; then
            APP_NAME="${{ env.DEV_APP_NAME }}"
            HOST_PORT="${{ env.DEV_HOST_PORT }}"
          else
            APP_NAME="${{ env.PROD_APP_NAME }}"
            HOST_PORT="${{ env.PROD_HOST_PORT }}"
          fi
          
          IMAGE_TO_DEPLOY="${{ env.DOCKER_REPO }}:${ROLLBACK_TAG}"
          
          echo "Rolling back to: $IMAGE_TO_DEPLOY"
          echo "Target environment: $TARGET_ENV"
          echo "Container name: $APP_NAME"
          echo "Port: $HOST_PORT"
          
          # ตัวอย่างคำสั่ง (ต้องใช้ self-hosted runner หรือ SSH)
          # docker pull $IMAGE_TO_DEPLOY
          # docker stop $APP_NAME || true
          # docker rm $APP_NAME || true
          # docker run -d --name $APP_NAME -p $HOST_PORT:8080 $IMAGE_TO_DEPLOY
      
      # Step 3: Send notification to n8n
      - name: Send rollback notification to n8n
        if: success()
        run: |
          TARGET_ENV="${{ github.event.inputs.rollback_target }}"
          if [ "$TARGET_ENV" == "dev" ]; then
            APP_NAME="${{ env.DEV_APP_NAME }}"
            HOST_PORT="${{ env.DEV_HOST_PORT }}"
          else
            APP_NAME="${{ env.PROD_APP_NAME }}"
            HOST_PORT="${{ env.PROD_HOST_PORT }}"
          fi
          
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Rollback ${TARGET_ENV^^}\",
              \"status\": \"success\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"${{ env.DOCKER_REPO }}:${{ github.event.inputs.rollback_tag }}\",
              \"container\": \"${APP_NAME}\",
              \"url\": \"http://localhost:${HOST_PORT}/\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"
  
  # =================================================================
  # JOB 7: NOTIFY ON FAILURE
  # =================================================================
  notify-failure:
    name: Notify on Failure
    runs-on: ubuntu-latest
    needs: [build-and-test, build-and-push-docker, deploy-dev, deploy-prod, rollback]
    if: failure()
    
    steps:
      - name: Send failure notification to n8n
        run: |
          TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
          curl -X POST ${{ secrets.N8N_WEBHOOK_URL }} \
            -H "Content-Type: application/json" \
            -d "{
              \"project\": \"${{ github.repository }}\",
              \"stage\": \"Pipeline Failed\",
              \"status\": \"failed\",
              \"build\": \"${{ github.run_number }}\",
              \"image\": \"N/A\",
              \"container\": \"N/A\",
              \"url\": \"N/A\",
              \"timestamp\": \"${TIMESTAMP}\"
            }" || echo "Failed to send notification"

```

**ความแตกต่างจาก Express/Flask**:

| ด้าน | Express/NodeJS | Flask/Python | Spring Boot/Java |
|------|----------------|--------------|------------------|
| **Setup** | `actions/setup-node@v4` | `actions/setup-python@v5` | `actions/setup-java@v4` |
| **Version** | Node.js 22 | Python 3.13 | Java 21 |
| **Distribution** | N/A | N/A | eclipse-temurin |
| **Package Manager** | npm | pip | Maven |
| **Dependencies File** | package.json | requirements.txt | pom.xml |
| **Lock File** | package-lock.json | (ไม่จำเป็น) | (ไม่จำเป็น) |
| **Cache** | `cache: 'npm'` | `cache: 'pip'` | `cache: 'maven'` |
| **Build Command** | `npm ci` / `npm install` | `pip install -r requirements.txt` | `mvn clean package` |
| **Test Framework** | Jest + Supertest | pytest | JUnit + Spring Boot Test |
| **Test Command** | `npm test` | `pytest -v --junitxml=...` | `mvn test` (รวมใน package) |
| **Artifact** | (ไม่จำเป็น) | (ไม่จำเป็น) | JAR file |
| **Port DEV** | 3001 | 5001 | 8081 |
| **Port PROD** | 3000 | 5000 | 8080 |
| **Project Detection** | (ไม่จำเป็น) | (ไม่จำเป็น) | ค้นหา pom.xml |

---

### 🔐 ขั้นตอนที่ 3: ตั้งค่า GitHub Secrets

**Secrets ที่จำเป็น** (เหมือน Express และ Flask):

1. **DOCKERHUB_USERNAME**: ชื่อผู้ใช้ Docker Hub
2. **DOCKERHUB_TOKEN**: Access Token จาก Docker Hub  
3. **N8N_WEBHOOK_URL**: URL สำหรับส่ง notification ไปยัง n8n (ถ้ามี)

**วิธีตั้งค่า Secrets**:

1. ไปที่ Repository ใน GitHub
2. คลิก **Settings** → **Secrets and variables** → **Actions**
3. คลิก **New repository secret**
4. เพิ่ม Secrets ทีละตัว (ใช้ค่าเดียวกับที่ตั้งไว้สำหรับ Express/Flask)

---

### 🎯 ขั้นตอนที่ 4: สร้าง Docker Hub Access Token

> ใช้ Token เดียวกับที่สร้างไว้สำหรับ Express/Flask ได้เลย หรือสร้างใหม่ก็ได้

ถ้ายังไม่มี ให้ทำตามขั้นตอน:

1. ไปที่ [Docker Hub](https://hub.docker.com/)
2. คลิกที่ **Account Settings** → **Security**
3. คลิก **New Access Token**
4. ตั้งชื่อ Token เช่น `github-actions-springboot`
5. เลือก Access permissions: **Read, Write, Delete**
6. คลิก **Generate**
7. **คัดลอก Token** (จะแสดงแค่ครั้งเดียว)
8. นำไปใส่ใน GitHub Secret `DOCKERHUB_TOKEN`

---

### 📊 ขั้นตอนที่ 5: ตั้งค่า GitHub Environments และ Approval Mechanism

**สร้าง Environment สำหรับ DEV และ PROD**:

1. ไปที่ Repository → **Settings** → **Environments**
2. คลิก **New environment**
3. สร้าง 3 environments:
   - **development**: สำหรับ DEV
   - **production-approval**: สำหรับ Approval Step
   - **production**: สำหรับ PROD

**ตั้งค่า Protection Rules สำหรับ Production Approval**:

1. เลือก **production-approval** environment
2. เปิดใช้ **Required reviewers** ✅
3. เพิ่ม Reviewers ที่ต้องอนุมัติก่อน deploy (แนะนำอย่างน้อย 2 คน)
4. (Optional) เปิดใช้ **Wait timer** เช่น 5-10 นาที
5. (Optional) ตั้งค่า **Deployment branches** → Selected branches → `main` เท่านั้น
6. คลิก **Save protection rules**

> **💡 หมายเหตุ**: Spring Boot ใช้ Approval Mechanism เหมือนกับ Express และ Flask ทุกประการ

---

### 🚀 ขั้นตอนที่ 6: Push Code และทดสอบ Workflow

1. **Commit และ Push โค้ด**:
   ```bash
   git add .github/workflows/main.yml
   git commit -m "Add GitHub Actions workflow for Spring Boot"
   git push origin develop
   ```

2. **ตรวจสอบ Workflow**:
   - ไปที่ Repository ใน GitHub
   - คลิกแท็บ **Actions**
   - จะเห็น Workflow กำลังรัน

3. **ดูผลลัพธ์**:
   - คลิกที่ Workflow run
   - ดู Logs ของแต่ละ Job
   - ตรวจสอบว่า Maven tests ผ่านหรือไม่
   - ตรวจสอบ JAR artifact ถูกสร้างหรือไม่

---

### 🔄 ขั้นตอนที่ 7: รัน Workflow และ Approval Process

**7.1 Build & Deploy แบบ Manual**:

1. ไปที่แท็บ **Actions**
2. เลือก Workflow **CI/CD - Spring Boot Docker App**
3. คลิก **Run workflow**
4. เลือก:
   - **Branch**: develop หรือ main
   - **Action**: Build & Deploy
   - (Optional) **project_dir_override**: ถ้า pom.xml ไม่อยู่ที่ root
5. คลิก **Run workflow**

**7.2 การอนุมัติ Production Deployment** (สำหรับ main branch):

เมื่อ Workflow รันถึง Job **Approval for Production** จะหยุดรอการอนุมัติ:

1. GitHub จะส่ง **Email notification** ให้ Reviewers
2. ไปที่แท็บ **Actions**
3. เลือก Workflow run ที่กำลังรอ (จะมีสถานะ **Waiting**)
4. คลิกปุ่ม **Review deployments** (สีเหลือง)
5. เลือก environment **production-approval**
6. (Optional) ใส่ comment เช่น "Approved for Spring Boot production deployment"
7. คลิก **Approve and deploy** (สีเขียว)
   - หรือ **Reject** (สีแดง) ถ้าไม่อนุมัติ

**ผลลัพธ์**:
- ✅ **Approve**: Workflow จะดำเนินการต่อไปยัง Job **Deploy to PROD**
- ❌ **Reject**: Workflow จะ fail และไม่ deploy

**7.3 Rollback แบบ Manual**:

1. ไปที่แท็บ **Actions**
2. เลือก Workflow **CI/CD - Spring Boot Docker App**
3. คลิก **Run workflow**
4. เลือก:
   - **Action**: Rollback
   - **rollback_tag**: ใส่ image tag (เช่น `a1b2c3d` หรือ `dev-123`)
   - **rollback_target**: เลือก `dev` หรือ `prod`
5. คลิก **Run workflow**

---

### 📸 ขั้นตอนที่ 8: หา Image Tag สำหรับ Rollback

**วิธีหา Image Tag** (เหมือน Express/Flask):

1. **จากหน้า Actions**:
   - ไปที่ Workflow run ที่ต้องการ
   - ดูใน Job "Build & Push Docker Image"
   - ดู Step "Set image tag" จะแสดง tag ที่ใช้

2. **จาก Docker Hub**:
   - ไปที่ [Docker Hub](https://hub.docker.com/)
   - เข้าไปที่ Repository `iamsamitdev/springboot-docker-app`
   - ดูรายการ Tags ที่มีอยู่

3. **จาก Git Commit**:
   - สำหรับ `main` branch: ใช้ Git short hash (7 ตัวแรก)
   ```bash
   git log --oneline
   # ตัวอย่าง: a1b2c3d Add new endpoint
   ```
   - สำหรับ `develop` branch: ใช้ `dev-{BUILD_NUMBER}`

---

### 🔍 ขั้นตอนที่ 9: ตรวจสอบและ Debug

**9.1 ดู Logs ของ Workflow**:

1. ไปที่แท็บ **Actions**
2. คลิกที่ Workflow run ที่ต้องการดู
3. คลิกที่ Job ที่ต้องการดูรายละเอียด
4. คลิกที่ Step เพื่อดู Logs

**9.2 Debug Mode**:

1. ไปที่ Repository → **Settings** → **Secrets and variables** → **Actions**
2. คลิก **Variables** tab
3. เพิ่ม Variable:
   ```
   Name: ACTIONS_STEP_DEBUG
   Value: true
   ```

4. รัน Workflow ใหม่ จะได้ Logs ละเอียดมากขึ้น

**9.3 ปัญหาที่พบบ่อยสำหรับ Spring Boot**:

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| `Error: Process completed with exit code 1` | Maven tests ล้มเหลว | ตรวจสอบโค้ดและ unit tests |
| `No such file or directory: pom.xml` | ไม่พบ pom.xml | ใช้ project_dir_override หรือย้าย pom.xml |
| `Error: buildx failed` | Docker build error | ตรวจสอบ Dockerfile และ JAR path |
| `Error: denied: requested access to the resource is denied` | Docker Hub credentials ผิด | ตรวจสอบ Secrets |
| `Java compilation error` | Code error | ตรวจสอบ Java source code |
| `Port 8080 already in use` | Port conflict | เปลี่ยน port หรือหยุด container เดิม |
| `No main manifest attribute` | JAR ไม่ executable | ตรวจสอบ spring-boot-maven-plugin |

---

### 📈 ขั้นตอนที่ 10: เพิ่ม n8n Notification

**10.1 สร้าง n8n Webhook**:

1. เปิด n8n Workflow Editor
2. เพิ่ม Node **Webhook**
3. ตั้งค่า:
   - **Method**: POST
   - **Path**: `/webhook/springboot-actions` (หรือใช้ path เดียวกับ Express/Flask)
4. คัดลอก **Production URL**

**10.2 เพิ่ม Secret ใน GitHub**:

```
Name: N8N_WEBHOOK_URL
Secret: https://your-n8n-instance.com/webhook/springboot-actions
```

> **💡 Note**: สามารถใช้ webhook URL เดียวกับ Express/Flask ได้ (แยกด้วย field `project`)

**10.3 Notification ถูกเพิ่มไว้ใน Workflow แล้ว**:

- ✅ Deploy to DEV success
- ✅ Deploy to PROD success
- ✅ Rollback success
- ✅ Pipeline failure

---

### 🎓 ขั้นตอนที่ 11: Best Practices สำหรับ Spring Boot

**11.1 Branch Strategy** (เหมือน Express/Flask):

- **develop**: สำหรับ Development → Deploy to DEV (port 8081)
- **main**: สำหรับ Production → Deploy to PROD (port 8080)
- **feature/***: สำหรับ Feature development → Run tests only

**11.2 Tagging Strategy** (เหมือน Express/Flask):

- **main branch**: ใช้ Git short hash (7 characters)
  - ตัวอย่าง: `a1b2c3d`
- **develop branch**: ใช้ `dev-{BUILD_NUMBER}`
  - ตัวอย่าง: `dev-123`

**11.3 Maven Configuration**:

- ใช้ **spring-boot-maven-plugin** สำหรับสร้าง executable JAR
- ตั้งค่า **maven-surefire-plugin** สำหรับ test reports
- (Optional) เพิ่ม **jacoco-maven-plugin** สำหรับ code coverage
- ใช้ **maven-failsafe-plugin** สำหรับ integration tests

**11.4 Testing Strategy**:

- ใช้ **JUnit 5** สำหรับ unit tests
- ใช้ **Spring Boot Test** สำหรับ integration tests
- ใช้ **TestContainers** สำหรับ testing กับ database/external services
- ใช้ **@SpringBootTest** สำหรับ full context tests

**11.5 Security**:

- ใช้ **Secrets** สำหรับข้อมูลที่เป็นความลับเสมอ
- อย่า hardcode API keys หรือ passwords ในโค้ด
- ใช้ **Environment protection rules** สำหรับ Production
- ใช้ **.gitignore** สำหรับไฟล์ที่ไม่ควร commit (target/, *.log, .env)

**11.6 Performance**:

- ใช้ **cache: 'maven'** สำหรับ Maven dependencies
- ใช้ **Docker layer caching** เพื่อเร่งความเร็ว build
- ใช้ **eclipse-temurin** JDK แทน Oracle JDK
- ใช้ multi-stage Docker build เพื่อลดขนาด image

---

### 📊 ขั้นตอนที่ 12: Monitor และ Analytics

**12.1 ดูสถิติ Workflow**:

1. ไปที่แท็บ **Actions**
2. ดู Workflow runs history
3. ตรวจสอบ:
   - **Success rate**
   - **Average run time**
   - **Failed runs**

**12.2 Test Results**:

1. เข้าไปดู Workflow run
2. ดู **Summary** tab
3. จะเห็น test results ที่ upload มา
4. คลิกดูรายละเอียด JUnit tests ที่ผ่านและไม่ผ่าน

**12.3 Artifacts**:

1. ดู **Artifacts** section ใน workflow run
2. Download **spring-boot-jar** เพื่อตรวจสอบ JAR file
3. Download **test-results** เพื่อดูรายงาน test ละเอียด

---

### 🔧 ขั้นตอนที่ 13: Deploy จริงด้วย Self-hosted Runner

**สำหรับการ Deploy ไปยัง Server จริง ต้องใช้ Self-hosted Runner**:

**13.1 ติดตั้ง Self-hosted Runner** (เหมือน Express/Flask):

1. ไปที่ Repository → **Settings** → **Actions** → **Runners**
2. คลิก **New self-hosted runner**
3. เลือก OS (Linux/macOS/Windows)
4. ทำตามคำสั่งที่แสดงบนหน้าจอ

**13.2 แก้ไข Workflow ให้ใช้ Self-hosted Runner**:

```yaml
deploy-dev:
  name: Deploy to DEV
  runs-on: self-hosted  # เปลี่ยนจาก ubuntu-latest
  needs: [build-and-test, build-and-push-docker]
  if: github.ref_name == 'develop'
  
  steps:
    - name: Deploy to DEV environment
      run: |
        docker pull ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
        docker stop ${{ env.DEV_APP_NAME }} || true
        docker rm ${{ env.DEV_APP_NAME }} || true
        docker run -d --name ${{ env.DEV_APP_NAME }} \
          -p ${{ env.DEV_HOST_PORT }}:8080 \
          ${{ env.DOCKER_REPO }}:${{ needs.build-and-test.outputs.image_tag }}
        docker ps --filter name=${{ env.DEV_APP_NAME }}
```

---

### 📚 สรุป Workflow

**Workflow นี้ประกอบด้วย**:

1. ✅ **Build & Test**: รัน Maven tests และสร้าง JAR
2. 🐳 **Build Docker Image**: สร้างและ push image ไปยัง Docker Hub
3. 🚀 **Deploy to DEV**: Deploy เมื่อ push ไปยัง `develop` branch (port 8081)
4. 🔐 **Approval for Production**: รอการอนุมัติจาก Reviewers (เฉพาะ `main` branch)
5. 🎯 **Deploy to PROD**: Deploy เมื่อ push ไปยัง `main` branch (port 8080, หลังจากได้รับการอนุมัติ)
6. 🔄 **Rollback**: Rollback ไปยังเวอร์ชันก่อนหน้า
7. 📢 **Notification**: ส่งการแจ้งเตือนไปยัง n8n

**Triggers**:
- ✅ **push** to develop/main
- ✅ **pull_request** to develop/main
- ✅ **workflow_dispatch** (Manual)

**Approval Mechanism**:
- 🔐 ใช้ **Environment Protection Rules** แทน `input` ของ Jenkins
- 👥 รองรับ **Multiple Reviewers** (1-6 คน)
- ⏱️ รองรับ **Wait Timer** (เวลารอก่อน deploy)
- 📧 ส่ง **Email Notification** อัตโนมัติ
- 📊 มี **Audit Log** ครบถ้วน

**Features เฉพาะ Spring Boot**:
- 🔍 **Auto-detect pom.xml** ในโฟลเดอร์ย่อย
- 📦 **JAR Artifact Upload/Download** 
- ☕ **Java 21 + Eclipse Temurin**
- 🏗️ **Maven Cache** เพื่อเร่งความเร็ว

---

### 🎯 ตัวอย่างการใช้งานจริง

**Scenario 1: Push Feature ไปยัง develop**
```bash
git checkout develop
git add .
git commit -m "Add new REST endpoint"
git push origin develop
```
→ Workflow จะรันอัตโนมัติ: Maven Tests → Build JAR → Build Docker → Deploy to DEV (port 8081)

**Scenario 2: Merge develop ไปยัง main (Production Deployment)**
```bash
git checkout main
git merge develop
git push origin main
```
→ Workflow จะรันอัตโนมัติ:
1. ✅ Maven tests และ package
2. ✅ Build Docker Image
3. ⏸️ **Approval for Production** (รอการอนุมัติ)
   - GitHub ส่ง email ให้ Reviewers
   - Reviewers ต้องไปอนุมัติที่ Actions tab
4. ✅ Deploy to PROD (port 8080, หลังจากอนุมัติ)

**Scenario 3: Rollback Production**
1. ไปที่ Actions tab
2. เลือก "CI/CD - Spring Boot Docker App"
3. คลิก "Run workflow"
4. ตั้งค่า:
   - Action: Rollback
   - rollback_tag: `a1b2c3d` (git hash ของเวอร์ชันก่อนหน้า)
   - rollback_target: `prod`
5. คลิก "Run workflow"

**Scenario 4: Custom Project Directory**
ถ้า pom.xml ไม่อยู่ที่ root:
1. ไปที่ Actions tab
2. คลิก "Run workflow"
3. ใส่ **project_dir_override**: `./backend` หรือ `./my-spring-app`
4. คลิก "Run workflow"

---

### 📖 ขั้นตอนที่ 14: เอกสารเพิ่มเติม

**สำหรับรายละเอียดเพิ่มเติมเกี่ยวกับ Approval Mechanism**:

ดูไฟล์ **GITHUB_ACTIONS_APPROVAL.md** ที่สร้างไว้ใน `express-docker-app/` ซึ่งใช้ได้กับ Spring Boot เช่นกัน:

- ✅ Step-by-step setup guide สำหรับ Environment และ Protection Rules
- ⚙️ Advanced options (Multiple approvers, Timeout, Custom messages)
- 🎨 Multiple approval levels (QA → Production)
- 📧 Notification setup (Email, Slack, Discord)
- 🔍 Troubleshooting common issues
- 📊 Best practices และ Security guidelines
- 🔄 เปรียบเทียบกับ Jenkins Approval

**ไฟล์ที่เกี่ยวข้อง**:
- `springboot-docker-app/.github/workflows/main.yml` - Workflow สำหรับ Spring Boot
- `springboot-docker-app/Jenkinsfile` - เปรียบเทียบกับ Jenkins
- `express-docker-app/GITHUB_ACTIONS_APPROVAL.md` - คู่มือการตั้งค่า Approval (ใช้ได้ทุกโปรเจกต์)

---

### 🔄 เปรียบเทียบ GitHub Actions vs Jenkins สำหรับ Spring Boot

| Feature | Jenkins (Jenkinsfile) | GitHub Actions (main.yml) |
|---------|----------------------|---------------------------|
| **Syntax** | Groovy DSL | YAML |
| **Setup Location** | Jenkinsfile | .github/workflows/main.yml |
| **Agent/Runner** | `agent any` | `runs-on: ubuntu-latest` |
| **Java Setup** | `docker.image('maven:3.9-eclipse-temurin-21').inside` | `actions/setup-java@v4` |
| **Project Detection** | `findFiles(glob: '**/pom.xml')` | `find . -name "pom.xml"` |
| **Maven Build** | `mvn -B -ntp clean package` | `mvn -B -ntp clean package` |
| **Working Directory** | `dir(env.PROJECT_DIR)` | `working-directory:` |
| **Docker Build** | `docker.build()` | `docker/build-push-action@v5` |
| **Docker Push** | `customImage.push()` | Built-in to build-push-action |
| **Artifacts** | `publishHTML()` + Custom | `actions/upload-artifact@v4` |
| **Test Results** | `junit 'target/surefire-reports/*.xml'` | Built-in JUnit support |
| **Approval** | `input message: "Deploy?"` | `environment: production-approval` |
| **Rollback** | Parameters + stages | workflow_dispatch inputs |
| **Notification** | Custom function + HTTP Request | curl to n8n webhook |
| **Secrets** | Jenkins Credentials | GitHub Secrets |
| **Environment** | Environment variables | env: block |
| **Conditional** | `when { expression }` | `if:` condition |
| **Cache** | Manual setup | `cache: 'maven'` (automatic) |

---

### Github Actions Self-hosted Runner บน Windows

> Self-hosted runner คือการนำเครื่องคอมพิวเตอร์ ของคุณเอง (ไม่ว่าจะเป็น PC, Server ในบริษัท, หรือ VM บน Cloud) มาติดตั้งโปรแกรมของ GitHub เพื่อให้มันทำหน้าที่เป็น 'ผู้ปฏิบัติงาน' สำหรับ GitHub Actions

> พูดง่ายๆ คือ แทนที่จะใช้เครื่องเซิร์ฟเวอร์มาตรฐานที่ GitHub เตรียมไว้ให้ (เรียกว่า GitHub-hosted runner) คุณเลือกที่จะใช้เครื่องของคุณเองในการรันขั้นตอน CI/CD (เช่น build, test, deploy) ทั้งหมด

1. ตั้งค่า Self-hosted Runner บน Windows:

   - ไปที่ Repository ของคุณบน GitHub
   - คลิกที่แท็บ "Settings"
   - ในเมนูด้านซ้าย เลือก "Actions" → "Runners"
   - คลิกที่ปุ่ม "New self-hosted runner"
   - เลือกระบบปฏิบัติการเป็น "Windows"
   - ทำตามคำแนะนำที่ปรากฏบนหน้าจอเพื่อดาวน์โหลดและตั้งค่า runner บนเครื่อง Windows ของคุณ

1.1 เปิด PowerShell (Run as Administrator): การรันสิทธิ์ Admin จะช่วยให้การติดตั้ง service หรือการเข้าถึง Docker ทำได้ง่ายขึ้น

```powershell
# 1. สร้างโฟลเดอร์
mkdir actions-runner; cd actions-runner

# 2. ดาวน์โหลด (ใช้ URL จากหน้าจอของคุณ)
Invoke-WebRequest -Uri https://github.com/actions/runner/releases/download/v2.329.0/actions-runner-win-x64-2.329.0.zip -OutFile actions-runner-win-x64-2.329.0.zip

# 3. แตกไฟล์
Add-Type -AssemblyName System.IO.Compression.FileSystem; [System.IO.Compression.ZipFile]::ExtractToDirectory("actions-runner-win-x64-2.329.0.zip", "$PWD")

```

1.2 กำหนดค่า Runner (Config):

```powershell
# เพิ่ม --labels self-hosted-windows-docker เข้าไป
.\config.cmd --url https://github.com/iamsamitdev/sample-github-action --token YOUR_TOKEN --name MyWindowsRunner --labels self-hosted-windows-docker
```
> การเพิ่ม label self-hosted-windows-docker จะทำให้เราสามารถระบุในไฟล์ .yml ได้ว่า "Job นี้ ต้องรันบน runner ที่มีป้ายกำกับนี้เท่านั้น"

1.3 รัน Runner:

```powershell
# รันแบบ interactive
.\run.cmd
# หรือรันเป็น service (แนะนำ)
.\svc install
.\svc start
```
> โปรแกรม runner จะเริ่มทำงานในหน้าต่าง PowerShell นี้และเชื่อมต่อกับ GitHub
> สำคัญ: เปิดหน้าต่างนี้ทิ้งไว้ตลอดการทดสอบ และต้องแน่ใจว่า Docker Desktop ของคุณกำลังทำงานอยู่

2. ปรับแต่งไฟล์ Workflow (.yml):

Job build-and-test และ build-docker: ยังคงเหมือนเดิม ปล่อยให้มันทำงานบน ubuntu-latest ของ GitHub ไป ซึ่งเป็นวิธีที่ดีและเร็วกว่าสำหรับการ build image

Job deploy (ที่เปลี่ยนชื่อเป็น deploy-to-windows):

เปลี่ยน runs-on: ubuntu-latest เป็น runs-on: self-hosted-windows-docker เพื่อบังคับให้ job นี้วิ่งมาที่เครื่อง Windows ของคุณ

ลบขั้นตอน actions/checkout@v4 ที่ไม่จำเป็นออก (เพราะเราไม่ต้องการโค้ด เราต้องการแค่ Docker image ที่ build เสร็จแล้ว)

เปลี่ยนขั้นตอน Deploy to server ให้เป็นคำสั่ง PowerShell ที่รันบนเครื่อง Windows ของคุณเพื่อสั่งงาน Docker Desktop

```yaml
# =================================================================
  # Job 4: Deploy (ปรับปรุงใหม่: ทำงานบนเครื่อง Windows ของคุณ)
  # =================================================================
  deploy-to-windows:
    name: Deploy to Local Windows Docker
    
    # 1. ระบุให้รันบน runner ที่เราเพิ่งสร้าง
    runs-on: self-hosted-windows-docker 
    
    needs: [build-docker, security-scan]
    if: github.ref == 'refs/heads/main' && (github.event_name == 'push' || github.event_name == 'workflow_dispatch')
    
    # 2. ใช้ environment 'production' (ไม่บังคับ แต่เป็น practice ที่ดี)
    environment:
      name: production
      url: http://localhost:3000 # URL ที่ทดสอบบนเครื่องคุณ
    
    steps:
      # 3. รันคำสั่ง PowerShell บนเครื่อง Windows ของคุณ
      - name: 🚀 Deploy to Docker Desktop
        # ใช้ 'shell: pwsh' เพื่อความชัดเจน (แม้ว่าจะเป็น default บน Windows runner)
        shell: pwsh 
        run: |
          echo "Starting deployment on Windows Self-Hosted Runner..."
          
          # 4. ดึง image ล่าสุดที่เพิ่ง build เสร็จ
          echo "Pulling latest image: ${{ env.DOCKER_IMAGE }}:latest"
          docker pull ${{ env.DOCKER_IMAGE }}:latest
          
          # 5. หยุดและลบ container เก่า (ถ้ามี)
          # ใช้ -ErrorAction SilentlyContinue เพื่อไม่ให้ script ล้มเหลวถ้าไม่มี container เก่า
          echo "Stopping and removing old container: ${{ env.CONTAINER_NAME }}"
          docker stop ${{ env.CONTAINER_NAME }} -ErrorAction SilentlyContinue
          docker rm ${{ env.CONTAINER_NAME }} -ErrorAction SilentlyContinue
          
          # 6. รัน container ใหม่
          echo "Running new container on port 3000..."
          docker run -d --name ${{ env.CONTAINER_NAME }} -p 3000:3000 --restart always ${{ env.DOCKER_IMAGE }}:latest
          
          echo "Deployment complete! Access at http://localhost:3000"
```

### สรุปการทำงาน (เมื่อคุณ Push Code)

1. **Job 1, 2, 3 (Build, Push, Scan):** จะทำงานบนเซิร์ฟเวอร์ ubuntu-latest ของ GitHub ตามปกติ GitHub จะ build โค้ดของคุณ, test, และ push Docker image ไปยัง Docker Hub

2. **Job 4 (Deploy):** เมื่องาน 3 Job แรกเสร็จ GitHub Actions จะเห็นว่า Job นี้ต้องรันบน self-hosted-windows-docker

3. **ส่ง Job:** GitHub จะส่งคำสั่งใน Job นี้มายังโปรแกรม run.cmd ที่คุณเปิดทิ้งไว้บนเครื่อง Windows

4. **Execute:** เครื่อง Windows ของคุณจะได้รับคำสั่ง และเริ่มรันสคริปต์ PowerShell นั้น, สั่ง docker pull, docker stop, docker rm, และ docker run บน Docker Desktop ของคุณโดยอัตโนมัติ

คุณก็จะเห็นแอปของคุณทำงานที่ http://localhost:3000 บนเครื่อง Windows ของคุณ
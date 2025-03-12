# Observability Stack

## 📌 Overview
Observability Stack provides monitoring and logging solutions for Kubernetes workloads using AWS CloudWatch, Prometheus, and Grafana.

## 🚀 Features
- **AWS CloudWatch for infrastructure monitoring**
- **Prometheus for Kubernetes metric collection**
- **Grafana for data visualization**
- **Helm charts for easy deployment**

## 📂 Folder Structure
```
observability-stack/
├── helm/        # Helm charts for monitoring stack
├── config/      # Configuration files for Prometheus & Grafana
├── scripts/     # Automation scripts
├── README.md    # Documentation
```

## 🛠 Prerequisites
- AWS CLI configured (`aws configure`)
- kubectl installed (`kubectl version`)
- Helm installed (`helm version`)
- EKS cluster running (`aws eks list-clusters`)

## ⚡ Deployment Steps

### **Step 1: Clone the Repository**
```sh
git clone https://github.com/your-org/observability-stack.git
cd observability-stack
```

### **Step 2: Configure AWS CloudWatch**
```sh
aws cloudwatch put-metric-alarm --alarm-name "HighCPU" \
    --metric-name "CPUUtilization" --namespace "AWS/EC2" \
    --statistic "Average" --threshold 80 --comparison-operator "GreaterThanThreshold" \
    --dimensions Name=InstanceId,Value=i-1234567890abcdef0 \
    --evaluation-periods 2 --alarm-actions arn:aws:sns:us-east-1:123456789012:MyTopic
```

### **Step 3: Deploy Prometheus & Grafana using Helm**
```sh
helm install prometheus prometheus-community/kube-prometheus-stack
```

### **Step 4: Access Grafana Dashboard**
```sh
kubectl port-forward svc/prometheus-grafana 3000:80
```
- Open `http://localhost:3000` in your browser
- Default credentials: **admin/admin**

## 🎯 Usage
- Monitor Kubernetes workloads and AWS infrastructure
- Set up alerts for high CPU/memory usage

## 🔄 Cleanup
To remove the monitoring stack:
```sh
helm uninstall prometheus
```

## 📖 Documentation
For more details, refer to [Prometheus Docs](https://prometheus.io/docs/) and [Grafana Docs](https://grafana.com/docs/).

## 📌 License
This project is licensed under the MIT License.


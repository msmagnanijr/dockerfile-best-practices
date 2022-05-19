https://github.com/aquasecurity/trivy

trivy image --severity HIGH,CRITICAL cloud-day
trivy fs --security-checks vuln,config .

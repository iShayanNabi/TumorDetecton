# TumorDetecton
**Brain Tumor Detection with Deep Learning and AWS**

This project aims to develop a deep learning-based approach for automatic brain tumor detection from MRI scans using AWS EC2 and S3.

**Requirements**

To run the code, you will need the following:

- Python 3.7 or higher
- AWS CLI
- AWS account with access to EC2 and S3 services
- Brain tumor classification dataset from [Kaggle](https://www.kaggle.com/sartajbhuvaji/brain-tumor-classification-mri)

**Setup**

1. Clone this repository:
```
git clone https://github.com/your_username/brain-tumor-detection.git
```

2. Create an AWS S3 bucket to store the dataset and related data:
```
aws s3api create-bucket --bucket my-bucket --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2
```

3. Upload the dataset to the S3 bucket:
```
aws s3 cp path/to/dataset s3://my-bucket/dataset --recursive
```

4. Create an EC2 instance with the appropriate configuration for running the code:
```
aws ec2 run-instances --image-id ami-0c55b159cbfafe1f0 --instance-type t2.micro --key-name my-key-pair --security-group-ids sg-xxxxxxxx --subnet-id subnet-xxxxxxxx --user-data file://path/to/install_script.sh
```

5. SSH into the EC2 instance and navigate to the project directory:
```
ssh -i path/to/my-key-pair.pem ec2-user@public-dns
cd /path/to/project
```

6. Install the required Python packages:
```
pip install -r requirements.txt
```

7. Modify the configuration file `config.py` with your own S3 bucket name, dataset directory path, and other relevant settings.

8. Run the code to train and evaluate the models:
```
python main.py
```

**Conclusion**

This project demonstrates the potential of deep learning-based approaches for brain tumor detection from MRI scans. By leveraging AWS EC2 and S3 services, we can train and evaluate models efficiently on large datasets. With further optimization and improvement, the proposed approach can assist clinicians and radiologists in the early detection and diagnosis of brain tumors, leading to improved patient outcomes.

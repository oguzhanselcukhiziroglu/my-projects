Clean-up
-------------------
1. CloudFront>>>>>Disable>>>>>>Delete
2. RDS 
3. RDS Subnet Group (After RDS Deleted)
4. Lambda Function
5. DynamoDB
6. R53 healthcheck
7. R53 failover records
8. S3 buckets (first objects)
9. IAM roles
10. NAT instance >>>>>terminate
11. ALB
12. TG
13. LT
14. ASG
15. Endpoint
16. internet gateway>>>>>detach>>>>>delete
17. subnets
18. private RT
19. VPC
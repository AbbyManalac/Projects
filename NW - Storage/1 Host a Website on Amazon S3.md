<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use S3 to host a static website. We're doing this project to learn about AWS and cloud services and how they can be used to store objects in the cloud and even host websites. 

### Tools and concepts

I used Amazon S3 for this project. Key concepts I learned include bucket policies, uploading static website files (like index.html), understanding bucket endpoint URLs, and how ACLs control access to objects within the bucket.

### Project reflection

This project took about 1.5 hours, including demo, quiz, and secret mission. The toughest part was fixing the 403 Forbidden error, but it was rewarding to see the website go live and publicly accessible.

---

## How I Set Up an S3 Bucket

Creating an S3 bucket took me less than 5 minutes. I needed to learn a few concepts like block public access and ACLs, but once that learning is done, I can create buckets in even shorter time in the future.

The Region I picked for my S3 bucket was Singapore because it's the region that closest to me. It's best practice to pick the region closest to you because it lowers time to retrieve your things.

S3 bucket names are globally unique! This means no two Amazon S3 buckets in the entire world can have the same name. They have to be completely unique, regardless of the region or the account ID.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### index.html and image assets

I uploaded two files to my S3 bucket - they were an index.html file (this determines the structure i.e. what goes inside the website) and a folder or images and assets (this will fill in the website with images and things to look at)

Both files are necessary for this project as index.html determines the structure, but the structure alone does not illustrate the content. You need to supply images and texts to make the website clearer, nicer, and more interactive. 

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

Website hosting means putting our website files on a web server, which is a special computer designed to turn our files into a website page that people can visit.

To enable website hosting with my S3 bucket, I went to the Properties tab of the bucket, enabled static website hosting and also labelled "index.html" as the Index document. 

An ACL is a way to configure permission settings inside a bucket. We enabled ACLs so that we can control access to the website files later. There was a popup mentioning that AWS recommends disabling ACLs, but keep it enabled to learn how ACLs work.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

Once static website is enabled, S3 produces a bucket endpoint URL, which is a URL that takes you (and anyone on the internet) to the website that you are hosting. 

I saw an error and it's because the objects in the bucket are public by default- though we've switched off "Block all Public Access". The website files are still private. We need to manage their access settings separately and need to be public too.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

To resolve this 403 Forbidden error, I updated the access settings of the files inside our bucket too. Using ACLs, I made the bucket's files public.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

---

---

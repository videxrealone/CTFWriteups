# CTFWriteups
Documenting My Tasks From Various CTF Competitions ( Still not updated )

# Cyberspark 2023
This event was a small CTF put together by Engineers Spark Iset'com in which we wrote some easy tasks for various categories in which the goal was to help people get into CTFs by giving them a glance at what they'll probably see in future CTFs.

* Flag Format: **Cyberspark{FLAG}**

## Forensics
For this CTF, I wrote 2 Forensics Tasks, The first being called "Mike's Investigation" which is a System Image and the second one is "Momento" which is a series of tasks that were intended to offer an intro to Memory Forensics.

## Mike's Investigation
In this task, the goal is to find some hidden information inside the user's documents.
The flag is split into 2 parts.

First of all we need to mount the Image to **FTK Imager**.
* **Link**: https://www.exterro.com/ftk-product-downloads/ftk-imager-version-4-7-1

* **Part I**:
In the task's description, I mentioned the word **personal files** and **top secret** which hints to **My Documents** and where we'll find a **TOP SECRET** folder.
![image](https://user-images.githubusercontent.com/91763346/236190527-1bcf3d79-1d8f-4fdb-b0ab-5fa69b753b2b.png)

Now in the top secret folder, we find a **galf.txt**, you guess it right, it's **flag.txt** but reversed and inside it we find the following content:
```
rC35_YM_6N1P33K{krapsrebyC // The idea here is that it's reversed and so we need to reverse it back.
```

The final result is:

```
Cyberspark{K33P1N6_MY_53Cr
```
Now that we have the first half of the flag, we can move to part II.

* **Part II**:

In the same folder, we can see another folder called **WHOLESOME MEMES** and a few images.

![image](https://user-images.githubusercontent.com/91763346/236191536-6e1fba84-abd7-4122-8f2c-811957af24cd.png)

Normally the players will start thinking that it's hidden with some sort of **steganography** and they're right.
Now they should extract those images and test them 1 by 1 with tools (online tools will do the job).

One of the most common used tools is : **AperiSolve** : https://www.aperisolve.com/

* **Link**: https://www.aperisolve.com/3ecb3637544fc59d1ae24d9695c7b5b9

![image](https://user-images.githubusercontent.com/91763346/236192518-b08b8598-c084-4db6-8694-cc52f8fee8b9.png)
When they reach the part where they upload the image **s3cr3t.jpg** to that website, they should find this.

In the **Exiftool** part, they will find some hidden base64 data within the **Comment** placeholder.

```
M0tkR01vVTNaRTR1YUE5YXp6ZGlXUENLeWlYRHAyNnRqeFpvdTF4b0ZJUHVqZjZEeDAxMHpDSUdJaGNHdnhKa1ZTRGI1N1VPMlkwQ3RtT1M0c3oyMUgzejc=
```

They now should either go with **https://dcode.fr** (that will stop giving correct values) or **https://gchq.github.io/CyberChef/** .

![image](https://user-images.githubusercontent.com/91763346/236193417-54f90822-109a-4716-8ab7-b9d2296daaef.png)

In this step they need to go from **base64** > **base62** > **base58** > **base45** > **base32** and they'll end up with the following decoded data: 

```
**375_H1DD3N_4W4Y}**
```

And the full flag is : **Cyberspark{K33P1N6_MY_53Cr375_H1DD3N_4W4Y}**

## Momento (Chained Series Task)


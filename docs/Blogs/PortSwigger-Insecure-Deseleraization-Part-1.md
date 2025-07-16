# PortSwigger Insecure Deseleraization Part 1

[**Lab: Modifying serialized objects | Web Security Academy**  
*This lab uses a serialization-based session mechanism and is vulnerable to privilege escalation as a result. To solve…*portswigger.net](https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects "https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects")

```
Lab:- Modifying serialized objects
Lab type:- APPRENTICE
```

This lab uses a serialization-based session mechanism and is vulnerable to privilege escalation as a result. To solve the lab, edit the serialized object in the session cookie to exploit this vulnerability and gain administrative privileges. Then, delete the user`carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

---

Lets Start doing the lab although the lab has solution i also wanted to make a walkthrough about the lab and so i did

Let’s start the first login into the Portswigger site and open the first lab Modifying serialized objects also start brupsuite and don’t yet start the intercept tab (Http History) will automatically login the request

![Open Lightbox](../assets/pslid1.webp){ .glightbox .center width="500" }


now click on my account page and open it with the given credential

![Open Lightbox](../assets/pslid2.webp){ .glightbox .center width="500" }

In the proxy tab click on the HTTP history click on the /my-account request and send it to the repeater tab by clicking the (ctrl + r) key or by right click mouse and send it to the repeater tab

now copy the cookie and open the decoder tab and paste the cookie in it and decode it as bas64 you will see the serialized form of the cookie

![Open Lightbox](../assets/pslid3.webp){ .glightbox .center width="500" }

Now in the cookie, the b represents a boolean value that is set to 0 which means false, let’s change it to 1 which means true and again encode it as base64, copy the manipulated cookie

now start the intercept tab and refresh the page now send the request to the repeater and remove the cookie value and paste the manipulated cookie value and send it

![Open Lightbox](../assets/pslid4.webp){ .glightbox .center width="500" }

Now see carefully that you have got an /admin panel link, which means that we have admin-level privileges now change the path of the page to /admin and send the request again and you will see 2 new links /admin/delete?username=weiner and /admin/delete?username=carlos so now again change the path to /admin/delete?username=carlos and send the request again you will see the account will be deleted and the lab will be solved

![Open Lightbox](../assets/pslid5.webp){ .glightbox .center width="500" }

I will also post one more labs related to Inscure Deserialization[](https://portswigger.net/web-security/deserialization)

Thank you for reading


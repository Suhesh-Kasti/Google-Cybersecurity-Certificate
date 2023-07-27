The internet is an open, public system with a lot of data flowing through it. Even though we all send and store information online, there's some information that we choose to keep private. In security, this type of data is known as personally identifiable information. *Personally identifiable information, or PII*, is any information that can be used to infer an individual's identity. This can include things like someone's name, medical and financial information, photos, emails, or fingerprints.

Maintaining the privacy of PII online is difficult. It takes the right security controls to do so. One of the main security controls used to protect information online is cryptography. *Cryptography* is the process of transforming information into a form that unintended readers can't understand. Data of any kind is kept secret using a two-step process: encryption to hide the information, and decryption to unhide it.
A **cryptographic key** is a mechanism that decrypts ciphertext. Every form of encryption relies on both a cipher and key to secure the exchange of information. Computers use a lot of encryption algorithms to send and store information online. They're all helpful when it comes to hiding private information, but only as long as their keys are protected. 

**Public key infrastructure, or PKI**, is an encryption framework that secures the exchange of information online. It's a broad system that makes accessing information fast, easy, and secure. So, how does it all work?

PKI is a two-step process. It all starts with the exchange of encrypted information. This involves either asymmetric encryption, symmetric encryption, or both.

**Asymmetric encryption** involves the use of a public and private key pair for encryption and decryption of data. Let's imagine this as a box that can be opened with two keys. One key, the public key, can only be used to access the slot and add items to the box. Since the public key can't be used to remove items, it can be copied and shared with people all around the world to add items. On the other hand, the second key, the private key, opens the box fully, so that the items inside can be removed. Only the owner of the box has access to the private key that unlocks it.

Using a public key allows the people and servers you're communicating with to see and send you encrypted information that only you can decrypt with your private key. This two-key system makes asymmetric encryption a secure way to exchange information online; however, it also slows down the process.

**Symmetric encryption**, on the other hand, is a faster and simpler approach to key management. Symmetric encryption involves the use of a single secret key to exchange information.

PKI uses both asymmetric and symmetric encryption, sometimes in conjunction with one another. It all depends on whether speed or security is the priority. For example, mobile chat applications use asymmetric encryption to establish a connection between people at the start of a conversation when security is the priority. Afterwards, when the speed of communications back-and-forth is the priority, symmetric encryption takes over.

While both have their own strengths and weaknesses, they share a common vulnerability, establishing trust between the sender and receiver. Both processes rely on sharing keys that can be misused, lost, or stolen. This isn't a problem when we exchange information in person because we can use our senses to tell the difference between those we trust and those we don't trust. Computers, on the other hand, aren't naturally equipped to make this distinction. That's where the second step of PKI applies. PKI addresses the vulnerability of key sharing by establishing trust using a system of digital certificates between computers and networks.

A *digital certificate* is a file that verifies the identity of a public key holder. Most online information is exchanged using digital certificates. Users, companies, and networks hold one and exchange them when communicating information online as a way of signaling trust. Let's look at an example of how digital certificates are created.
Digital certificates are a lot like a digital ID badge that's used online to restrict or grant access to information. This is how PKI solves the trust issue. Combined with asymmetric and symmetric encryption, this two-step approach to exchanging secure information between trusted sources is what makes PKI such a useful security control.
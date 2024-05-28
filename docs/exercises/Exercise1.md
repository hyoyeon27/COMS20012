# Exercises Sheet 1

## Intro to CIA/AAA/Threat/Security Principles

1. **Let us assume that the mayor of Bristol wants to release a public notice on an important issue. Which of the CIA properties should be enforced and why?**
   - **ANS A.1:** Integrity and Availability. **I** because none should be able to alter it in an unintended way and **A** because it should be available to the public to see.

2. **Explain why someone need not worry about being a victim of a social engineering attack through their cell phone if they are inside of a Faraday cage.**
   - **ANS A.2:** Because there will be no signal to get connected to the site if that was the intention of the attacker.

3. **With respect to the C.I.A. and A.A.A. concepts, what risks are posed by Trojan horses?**
   - **ANS A.3:** A Trojan horse can violate all of the CIA, by leaking information, modifying files, and deleting files. For AAA, it can sabotage authenticity.

4. **With respect to the C.I.A. and A.A.A. concepts, what risks are posed by someone making so many download requests from an online music store that it prevents other users from being able to download any songs?**
   - **ANS A.4:** CIA - Availability, AAA - Accountability.

5. **Give an example of the false sense of security that can come from using the “security by obscurity” approach.**
   - **ANS A.5:** Using an encryption scheme that is not public, thinking that no one will break it if they don't know about it. Another example is hard-coded secrets in the binary thinking that no one will know about them.

6. **The HF Corporation has a new refrigerator, the Monitator, which has a camera that takes a picture of the contents of the refrigerator and uploads it to the HF Corporation’s web site. The Monitator’s owner can then access this web site to see what is inside their refrigerator without opening the door. For security reasons, the HF Corporation encrypts this picture using a proprietary algorithm and gives the 4-digit PIN to decrypt this picture to the Monitator’s owner, so he or she can get access to the pictures of their Monitator’s interior. What are the security concerns and principles that this solution does and doesn’t support?**
   - **ANS A.6:** It is a simple design, thus the *economy of mechanism* principle is followed. However, a proprietary encryption scheme is a bad idea (*open design* principle). Protecting it with a PIN is good (confidentiality and assurance). However, a 4-digit PIN may be weak protection.

7. **Consider a desktop publishing system used to produce documents for various organizations.**
   - a. **Give an example of a type of publication for which confidentiality of the stored data is the most important requirement.**
     - **ANS A.7.a:** The system will have to assure confidentiality if it is being used to publish corporate proprietary material.
   - b. **Give an example of a type of publication in which data integrity is the most important requirement.**
     - **ANS A.7.b:** The system will have to assure integrity if it is being used to publish laws or regulations.
   - c. **Give an example in which system availability is the most important requirement.**
     - **ANS A.7.c:** The system will have to assure availability if it is being used to publish a daily paper.

8. **For each of the following assets, assign a low, moderate, or high impact level for the loss of confidentiality, availability, and integrity, respectively. Justify your answers.**
   - a. **An organization managing public information on its Web server.**
     - **ANS A.8.a:** An organization managing public information on its web server determines that there is no potential impact from a loss of confidentiality (i.e., confidentiality requirements are not applicable), a moderate potential impact from a loss of integrity, and a moderate potential impact from a loss of availability.
   - b. **A law enforcement organization managing extremely sensitive investigative information.**
     - **ANS A.8.b:** A law enforcement organization managing extremely sensitive investigative information determines that the potential impact from a loss of confidentiality is high, the potential impact from a loss of integrity is moderate, and the potential impact from a loss of availability is moderate.
   - c. **A financial organization managing routine administrative information (not privacy-related information).**
     - **ANS A.8.c:** A financial organization managing routine administrative information (not privacy-related information) determines that the potential impact from a loss of confidentiality is low, the potential impact from a loss of integrity is low, and the potential impact from a loss of availability is low.
   - d. **An information system used for large acquisitions in a contracting organization contains both sensitive, pre-solicitation phase contract information and routine administrative information. Assess the impact for the two data sets separately and the information system as a whole.**
     - **ANS A.8.d:** The management within the contracting organization determines that:
       - (i) For the sensitive contract information, the potential impact from a loss of confidentiality is moderate, the potential impact from a loss of integrity is moderate, and the potential impact from a loss of availability is low.
       - (ii) For the routine administrative information (non-privacy-related information), the potential impact from a loss of confidentiality is low, the potential impact from a loss of integrity is low, and the potential impact from a loss of availability is low.
   - e. **A power plant contains a SCADA (supervisory control and data acquisition) system controlling the distribution of electric power for a large military installation. The SCADA system contains both real-time sensor data and routine administrative information. Assess the impact for the two data sets separately and the information system as a whole.**
     - **ANS A.8.e:** The management at the power plant determines that:
       - (i) For the sensor data being acquired by the SCADA system, there is no potential impact from a loss of confidentiality, a high potential impact from a loss of integrity, and a high potential impact from a loss of availability.
       - (ii) For the administrative information being processed by the system, there is a low potential impact from a loss of confidentiality, a low potential impact from a loss of integrity, and a low potential impact from a loss of availability.

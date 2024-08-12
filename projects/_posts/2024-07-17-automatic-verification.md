---
layout: post
title: Automatic Formal Specification Generation And Verification
image:
    path: /assets/img/blog/automatic-verification-home.jpg
description: >
  Master thesis project for the degree program M.Sc Autonomous Systems in colloboration with ThoughtWorks
sitemap: true
comments: true
---

{:.lead}

- Table of Contents
{:toc .large-only}

<!-- Intro paragraph, what is this blog about? -->
Let me start by asking you this question. Do you know if the neural network you developed work as you intended? You might have used a verification dataset to check if your model has generalized well to unseen data. But is that enough to know if the neural network's functionality is correct and complete? What if the network is going to be deployed in a safety ctitical system like autonomous cars? Will the usual verification dataset be enough to guarantee the functionalities? It is absolutely necessary to make sure that the software present in autonomous vehicles have no functional faults for the safety of the passengers in it.

## Background and problems
<!-- Safety standards and the v-model -->
Automotive industry is very well regulated by both the government and industry consortiums, to make sure safety is a priority when manufacturing vehicles. Best practices in the industry are captured in the form of safety standards. One of the most well-known safety standard is the [ISO 26262](https://www.iso.org/standard/68383.html) which deals with the functional safety of the E/E systems of the car, including both hardware and software. It covers the overall product development lifecycle from specification, design, implementation, integration, verificationa, validation and product release. The standard follows the V-model of systems engineering process. One of the core concepts anchoring the v-model is verification and validation.

{% include image.html url="../../assets/img/blog/v-model.jpeg" description="V-model of systems engineering process" %}

<!-- Verification and validation, problems in AI V&V -->
Verification is the process of checking if our system is built in accordance with the given requirement and specifications. Validation is the process of checking if the specified requirements meet the needs of the intended task or the customer. In other words, verification is answering the question, "Are we building the product right?" and validation answers the question "Are we building the right product?". Verification and Validation (V&V) plays an important role in assessing safety and building trust in a system. Currently available methods for V&V fall short when it comes to software systems with AI in it. And the contribution of AI in cars are constantly increasing from smart climate control to powering the autonomous driving functionality.

<!-- Problems -->
About 90% of all road accidents are attributed to human error and automating the driving task itself can save many lifes. The task of replacing the driver with an automated system is not easy. Automakers need to be sure themselves and prove it to their customers that they can trust the vehicle with their lives. Current industry practice in testing the functionality of the vehicle is conduct extensive testing in simulations and in real world. The problem with this approach is that this approach is very resource intensive. According to this [research](https://www.rand.org/content/dam/rand/pubs/research_reports/RR1400/RR1478/RAND_RR1478.pdf) it would take hundreds of millions of miles and sometimes hundreds of billions of miles for a autonomous vehicle to demonstrate their performance in terms of fatalities and injuries. How long would it take to complete all these miles before a self-driving technology can hit the roads. As it stands, about 90% of the self-driving problem is already solved but we can't guarantee that it will be safe in all driving conditions. Developers of these technologies make sure to collect diverse data and train their system on it to make sure they perform equally well in all situations.

We need better methods that can complement simulation-based and real-world testing. Formal methods seems to be promising in that area with their ability to provide us with mathematical proofs which can eliminate the need for extensive testing. As most of the researchers are concentrating in developing the technology that makes the cars drive themselves, I decided to work on methods to verify if they are safe for my masters thesis. Perception is usually the bottleneck for autonomous driving technology, as it affects all other systems in a chain reaction. Several works in verifying the perception systems exist and they mostly focus on verifing if the perception system is robust to input changes. Very little works exist in trying to verifying the functionality of the perception systems. For example, did an object detection module classify an object as a car based on the right reasons? Did it learn to recognize a car correctly? These are some of the questions we would be interested in verifying.

## Goal
On investigating why verification is hard for AI-based systems, the following problems were found.

**1. AI is a blackbox** <br>
Neural networks are often used in perception systems for object detection and tracking. They are opaque systems, meaning their decision making process is not seen. This makes functional verification difficult. Explainable AI, a whole new field has emerged to develop AI systems that are explainable, which would make the verification process much easier.

**2. Validatity of verification** <br>
As mentioned earlier, AI systems are usually verified using simulation-based testing and real-world testing. But the validity of those verification becomes obsolete when the model is updated. All the situations that was driven in simulations and in real-world needs to be driven again to make sure the system performs well after the changes. We would need automation tools that will automatically verify and validate these systems when updated. Such automatic tools in combination with formal methods based verification can verify the systems effectively and much faster. Today, there are not many tools that are capable of continuous verification.

**3. Lack of formal specifications** <br>
Verification is the process of checking if our system is built in accordance with the given requirements and specifications. For it to be effective, we need to set correct set of requirements for the system. For effective formal verification, the specifications used to verify also needs to be specified formally. They are called as formal specifications. Now the problem is, how will we formally specify the expected behaviour of a perception system. For example, let's say our system needs to correctly identify and classify all pedestrians on the road. How will we specify this requirement formally?

The goal of this thesis is to contribute towards solving all of these issues in such a way that the autonomous vehicles homologation process is improved. To that end, a framework was created that will continuously verify neural network based object detection modules. The framework takes in an ontology of the world in which the model is going to be deployed. Eg: An ontology that models all the objects that a car might encounter in its driving environments. The framework parses the ontology and creates syntactically and semantically correct formal specifications in a language called Conspec. For verification, the framework uses a VLM (CLIP) to verify if the model satisfies the generated Conspec specifications.

You can read more about my thesis here <br>

[thesis.pdf](../../assets/files/thangaraj_kalaiselvan_thesis.pdf)


<br>
<br>

<!-- {% if page.comments %}
<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    /*
    var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = 'https://ks-disqus-com.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %} -->
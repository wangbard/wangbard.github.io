---
# the default layout is 'page'
title: About Me
icon: fas fa-info-circle
order: 4
---

My name is **Mingrui Zou**, and I am currently pursuing a Master’s in Cybersecurity at The University of Edinburgh. My thesis focuses on secure multiparty computation (MPC) combiners under the supervision of Dr. Michele Ciampi. Prior to this, I completed my Bachelor’s degree in Computer Science and Artificial Intelligence at The University of Edinburgh, where my undergraduate thesis, supervised by Prof. Chris Heunen and Dr. Robin Kaarsgaard, examined the topic of quantum information effects. My academic journey has led me to explore the intersection of quantum computing and cryptography, particularly in their applications to secure communication systems.

> 🔑 **My PGP Fingerprint**  
> `E149 B1A3 F402 5B79 77EC F94D B29A F9E5 93DF 06E7`   
> 📥 **[Download Public Key](/files/wangbard_0x93DF06E7_public.asc)**  
{: .prompt-info }


## **Research Interests**

My research interests span both **cryptography** and **quantum computing**, with a particular focus on post-quantum cryptography and quantum algorithms. I am actively seeking a **Ph.D.** position to further explore these areas and contribute to advancements in quantum technologies and secure systems as we move toward a quantum-powered future.

## **Education**

**The University of Edinburgh**  
*Master of Science in Cybersecurity, Privacy and Trust*  
_09/2023 - 11/2024_ - **MSc With Distinction**
- **Thesis title**: Multiparty Computation Combiners.

**The University of Edinburgh**  
*Bachelor of Science with Honours in Artificial Intelligence and Computer Science*  
_09/2018 - 07/2023_ - **Upper Second-Class Honours**
- **Thesis title**: Helping Yuppies on Quantum Information Effects.


## **Thesis Projects**

### Multiparty Computation Combiners _(2024/04 - 2024/08)_

In my Master's thesis, supervised by Dr. Michele Ciampi, I investigated the construction of cryptographic combiners for secure multiparty computation (MPC). Given that Oblivious Transfer (OT) is a fundamental building block in many MPC protocols—and that previous research has shown the impossibility of transparent black-box construction for 1-out-of-2 OT combiners—the design of secure MPC combiners poses unique challenges. In this research, I introduce the first formal definition of black-box MPC combiners, which ensure that secure computation can still be achieved even if some underlying protocols fail, as long as a subset of the candidates remains reliable. A key contribution is the design and analysis of a 1-out-of-2 MPC combiner that securely computes a function for two parties under semi-honest setting using two candidate MPC protocols, under the assumption that at least one remains secure. Through rigorous cryptographic analysis, employing simulation-based security proofs and theorems, the combiner’s design was validated to ensure security for at least one party. I also discussed the inherent limitations in achieving full two-party security under two protocols. Building on the this, I developed a 2-out-of-3 MPC combiner that requires at least two out of three candidate protocols to remain secure. I examined the vulnerabilities of this approach and proposed an alternative construction that, while less efficient, provides robust security guarantees.

> 📄 **My MSc Dissertation on** ***Multiparty Computation Combiners***  
> If you are interested, you may [read the full dissertation here](/files/Multiparty_Computation_Combiners.pdf).
{: .prompt-info }

### Helping Yuppies on Quantum Information Effects _(2022/09 - 2023/04)_

This undergraduate thesis, supervised by Prof. Chris Heunen, focused on analyzing the type-and-effect interpretation of measurement as introduced in his paper *"Quantum Information Effects"*. The study formulated measurement as a computational effect, involving both the introduction of ancilla systems (allocation) and the selective reduction of information (hiding) to exploit the purification of quantum states. In my thesis, a Haskell program was developed based on the proposed categorical semantics to calculate the minimum number of ancilla (auxiliary qubits) required for measurement as a quantum information effect, demonstrating the practical application of these theoretical concepts. Additionally, a mathematical proof was formulated to elucidate the relationship between the minimum number of ancilla qubits needed and the von Neumann entropy of the system.

## MISC

<style>
/* Custom skill bar styles for about.md */
.skills {
    max-width: 500px;
    margin-top: 20px;
}

.skill {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
}

.skill span {
    width: 100px; /* Label width */
    font-weight: bold;
}

.skill-bar {
    flex: 1;
    height: 10px;
    background-color: #ddd;
    border-radius: 5px;
    margin-left: 10px;
    position: relative;
}

.skill-bar::before {
    content: '';
    position: absolute;
    height: 100%;
    background-color: #4CAF50; /* Customize the color */
    border-radius: 5px;
    transition: width 0.3s ease;
    width: inherit;
}
</style>

### Programming Skills
<div class="skills">
    <div class="skill">
        <span>Python</span>
        <div class="skill-bar" style="width: 90%;"></div>
    </div>
    <div class="skill">
        <span>Java</span>
        <div class="skill-bar" style="width: 80%;"></div>
    </div>
    <div class="skill">
        <span>Haskell</span>
        <div class="skill-bar" style="width: 70%;"></div>
    </div>
    <div class="skill">
        <span>C</span>
        <div class="skill-bar" style="width: 55%;"></div>
    </div>
</div>

### Rubik's Cube

> 🧩 **Rubik's Cube Journey**  
> When I was young, I felt quite proud of myself when I managed to restore one face of a Rubik's Cube. Later, I discovered a guide that came with the cube, teaching how to solve all six faces. I still remember the sense of accomplishment when I first solved it completely. In an algebra course, my friend and I took this interest further by creating a Jupyter notebook to explore the cube’s group structure. [Check it out here](https://github.com/wangbard/Rubik-s-Cube).


### Gaming

> 🎮 **My Steam Profile**  
> I'm more of a casual gamer, but if you'd like to connect, feel free to reach out to me on [my Steam profile](https://steamcommunity.com/profiles/76561198864699098/).
{: .prompt-info }

<div class="gaming-ranks">
    <div class="rank">
        <div class="rank-title">League of Legends</div>
        <div class="rank-bar">
            <div class="rank-bar-fill lol-bar">Diamond 2</div>
        </div>
    </div>
    <div class="rank">
        <div class="rank-title">Dota 2</div>
        <div class="rank-bar">
            <div class="rank-bar-fill dota-bar">3600 MMR</div>
        </div>
    </div>
</div>

> 🎮 **Fun Fact**  
> Some people assume my gaming ID, *Wangbard*, means my family name is Wang. Actually, *Bard* is my favorite champion in League of Legends, and *Wang* means "king" in Chinese—so *Wangbard* playfully implies "King of Bard." League used to be my favorite game, and I have spent thousands of hours on it. These days, I only play very occasionally with friends, but it still holds a special place in my memories.

<style>
/* Fancy Gaming Rank Styles with Hover Tooltip */
.gaming-ranks {
    max-width: 600px;
    margin-top: 20px;
    font-family: Arial, sans-serif;
}

.rank {
    margin-bottom: 25px;
    font-weight: bold;
}

.rank-title {
    font-size: 1.1em;
    margin-bottom: 5px;
}

.rank-bar {
    position: relative;
    height: 25px;
    width: 100%;
    background: linear-gradient(to right, #ddd, #bbb);
    border-radius: 12px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.3);
}

.rank-bar-fill {
    position: absolute;
    height: 100%;
    border-radius: 12px;
    text-align: right;
    color: white;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding-right: 10px;
    font-size: 0.9em;
    transition: width 0.3s ease;
}

.lol-bar {
    width: 80%; /* Adjust width based on rank */
    background: linear-gradient(to right, #4B79A1, #283E51);
}

.dota-bar {
    width: 60%; /* Adjust width based on rank */
    background: linear-gradient(to right, #FF512F, #DD2476);
}

/* Tooltip Style */
.rank-bar:hover::after {
    content: attr(data-tooltip); /* Tooltip content */
    position: absolute;
    left: 50%;
    top: -35px;
    transform: translateX(-50%);
    background-color: rgba(0, 0, 0, 0.8);
    color: #fff;
    padding: 5px 10px;
    border-radius: 5px;
    font-size: 0.9em;
    white-space: nowrap;
    opacity: 1;
    transition: opacity 0.3s ease;
    pointer-events: none;
}

.rank-bar::after {
    opacity: 0;
}
</style>


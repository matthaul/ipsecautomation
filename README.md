<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Thanks again! Now go create something AMAZING! :D
***
***
***
*** To avoid retyping too much info. Do a search and replace for the following:
*** matthaul, ipsecautomation, matthaul, matthaul@gmail.com, IPsec Automation, Automate ipsec tunnel vpn. Improve readability for tunnel statuses. Create a set it and forget it, tunnel monitor/keep alive service.
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/matthaul/ipsecautomation">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">IPsec Automation</h3>

  <p align="center">
    Automate ipsec tunnel vpn. Improve readability for tunnel statuses. Create a set it and forget it, tunnel monitor/keep alive service.
    <br />
    <a href="https://github.com/matthaul/ipsecautomation"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/matthaul/ipsecautomation">View Demo</a>
    ·
    <a href="https://github.com/matthaul/ipsecautomation/issues">Report Bug</a>
    ·
    <a href="https://github.com/matthaul/ipsecautomation/issues">Request Feature</a>
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

A tool to help tunnel administrators report and automate management of ipsec connections and tunnels.
The first problem to solve is determine when an ipsec conn or a tunnel within that connection is down. Then bringing that tunnel up and doing so in such a way that does not require setting up IP addresses to monitor. The config file already knows what you are trying to do.

## ipsectun
Function
* Get and report total, up, and down conns running via ipsec. Excluding conns that the user specified.
* If tunnel is down report ipsec conn name and run ipsec auto --up for each down conn identified.
* Recheck totals

Problem
* ipsec can and will bring back up a non established conn but if it fails too many times it appears to stop trying. 

Solution
* This script solves that by finding and upping the down conn 
* Adding a cron job automates it.

### Built With

* [bash](https://www.gnu.org/software/bash/)

<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple steps.

### Prerequisites

ipsec
*   conn added and up
*   identify the full path of the ipsec executable 
    
    (default for centos)
    ```sh
    /usr/sbin/ipsec
    ```
Environment
*   linux running GNU bash

### Installation

You can get the script [here](ipsectun/ipsectun). 
*   Add your path to ipsec IPSECCCMD variable if your path is not default.
*   Add your excluded conn names to the EXCLUDEDCONNSARRAY

To make it quick and easy to run do the following

1. Create the file, make it executable, create a simlink (CentOS)
   ```sh
    #Make an ipsectun file
    touch /usr/local/sbin/ipsectun
    
    #make ipsectun executable
    chmod 755 /usr/local/sbin/ipsectun
    
    #make a symlink to the file
    ln -s /usr/local/sbin/ipsectun ipsectun
   ```
2. Populate the file with your modified script: Base ipsectun script [here](ipsectun/ipsectun)
   ```sh
   vim ipsectun
   ```
3.  (Optional) Automate it with crontab and log last output
    ```sh
    crontab -e

    # Monitor and fix down ipsec conns/tunnels
    */5  * * * * /usr/local/sbin/ipsectun > /var/log/ipsectunlastrun.log
    ```



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

### Example 1
Case: All tunnels are up
*   Run
    ```sh
    ipsectun
    ```
*   Result
    ```sh
    
    ```

### Example 2
Case: Some tunnels are down
*   Run
    ```sh
    ipsectun
    ```
*   Result
    ```sh
    
    ```


<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/matthaul/ipsecautomation/issues) for a list of proposed features (and known issues).



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact

Matt Hall - [@matthaul](https://twitter.com/matthaul) - matthaul@gmail.com

Project Link: [https://github.com/matthaul/ipsecautomation](https://github.com/matthaul/ipsecautomation)



<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements

* []()
* []()
* []()





<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/matthaul/ipsecautomation.svg?style=for-the-badge
[contributors-url]: https://github.com/matthaul/ipsecautomation/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/matthaul/ipsecautomation.svg?style=for-the-badge
[forks-url]: https://github.com/matthaul/ipsecautomation/network/members
[stars-shield]: https://img.shields.io/github/stars/matthaul/ipsecautomation.svg?style=for-the-badge
[stars-url]: https://github.com/matthaul/ipsecautomation/stargazers
[issues-shield]: https://img.shields.io/github/issues/matthaul/ipsecautomation.svg?style=for-the-badge
[issues-url]: https://github.com/matthaul/ipsecautomation/issues
[license-shield]: https://img.shields.io/github/license/matthaul/ipsecautomation.svg?style=for-the-badge
[license-url]: https://github.com/matthaul/ipsecautomation/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/matthaul
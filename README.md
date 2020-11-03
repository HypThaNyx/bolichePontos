<h2 align="center"> BolichePontos </h2>

<p align="center">
This repo should auxiliate on the counting of score in bowling. It uses a .NET Core ClassLib for the logic and xUnit for Unit Testing.
</p>

<p align="center">
  <a href="https://github.com/HypThaNyx">
    <img alt="Made by Wesley Yago" src="https://img.shields.io/badge/made%20by-Wesley%20Yago-orange">
  </a>

  <img alt="Last Commit" src="https://img.shields.io/github/last-commit/HypThaNyx/bolichePontos">

  <img alt="Contributors" src="https://img.shields.io/github/contributors/HypThaNyx/bolichePontos">

  <img alt="License" src="https://img.shields.io/badge/license-MIT-orange">

  <a href="https://www.linkedin.com/in/wesley-yago-da-silva/">
    <img alt="Check out my LinkedIn!" src="https://img.shields.io/badge/-LinkedIn-black.svg?logo=linkedin&color=666">
  </a>
</p>

---

## Table of Contents

<ul>
  <li><a href="#-how-it-works">How it works</a></li>
  <li><a href="#-getting-started">Getting Started</a></li>
  <li><a href="#-features">Features</a></li>
  <li><a href="#-support">Support</a></li>
  <li><a href="#-license">License</a></li>
</ul>

---

## 🎳 How it works

### Rules

The bowling score system works with the following rules:
- the more pins knocked down with the least number of attempts (throws), the bigger the score
- each game has always 10 frames
- when the player knocks down 10 pins in a single throw, it's a strike
- when the player knocks down 10 total pins in different throws but in the same frame, it's a spare
- at each of the first 9 frames the player has 10 pins to knock down and:
  - only 1 throw if the first ball hits a strike, or
  - 2 throws if it doesn't
- at the frame 10 the player has 10 pins to knock down (that are restored after each strike/spare) and:
  - only 2 throws if none of the balls hit a strike or a spare, or
  - 3 throws if at least one of them do
- each pin knocked down is worth a point, but:
  - every strike multiplies the score of the next 2 throws on the next frame, and
  - every spare multiplies the score of the next throw on the next frame

### Situations

Expressions used in this section:

- <b>normal throw</b>: a ball thrown that hasn't scored a strike nor a spare.
- <b>special throw</b>: a ball that has scored either a strike or a spare.

A normal match with <b>no special throws</b> should last 20 throws.

An 'extended match' would be one where a <b>special throw</b> of any kind is reached at the 10th frame, resulting in an extra throw.

The least amount of score is 0 (all misses) and the highest is 300 (perfect match with 12 strikes).

The least amount of throws is 11 (9 strikes followed by 2 <b>normal throws</b> at the 10th) and the highest is 21 (18 <b>normal throws</b> followed by a <b>special throw</b> at the 10th frame).

Two strikes in sequence should multiply the score of the next throw by 3.

### Test Cases

- [X] Should score 0 for gutter game (all losses).
- [X] Should score 20 for simple game (all ones).
- [X] Should score 16 for a spare followed by a 3 ball
( [ 4️⃣ + 6️⃣ ] + 3️⃣ )
- [X] Should score 24 for a strike followed by a 3-point and a 4-point ball ( 🔟 + [ 3️⃣ + 4️⃣ ] )
- [X] Should score 23 for two sequential spares ( [ 4️⃣ + 6️⃣ ] + [ 3️⃣ + 7️⃣ ] )
- [X] Should score 300 for a perfect game (12 strikes)
- [X] Should score 30 for a strike followed by a spare ( 🔟 + [ 5️⃣ + 5️⃣ ] )
- [X] Should score 270 for 9 strikes followed by 5-point balls thrown 3 times at the 10th frame ( [ 9️⃣ * 10 ] + [ 5️⃣ + 5️⃣ + 5️⃣ ] )


---

## 🚀 Getting Started

### Prerequisites

- [.NET Core 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)

### Setup

Instructions to use:
- download or clone the repo
- run a Shell prompt inside the project's main folder (bolichePontos)
- enter the following command and press Enter:

``` bash
dotnet test
```

- voilà!

---

## 📋 Features

The program should be able to:
- [X] Calculate the amount of score for games with no strikes or spares.
- [X] Calculate the effect of strikes and spares on the score.
- [X] Execute Unit Testing through xUnit and test the test cases described on this document.
- [X] Elaborate a full-covered Coverage Report.

The main idiom used is `[🇧🇷] Brazilian Portuguese`, my mother tongue.

## Steps To Generate Coverage Reports

1. Create a terminal instance in your tests project folder
2. Add the coverlet package to your project (this command has already been run in this project)

    ``` bash
    dotnet add package coverlet.msbuild
    ```

3. Install the dotnet reportgenerator to generate HTML previews of the coverage report

    ``` bash
    dotnet tool install -g dotnet-reportgenerator-globaltool
    ```

4. Run the test command with this parameter to generate the coverage report

    ``` bash
    dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=lcov /p:CoverletOutput=./lcov.info ./bolicheTests
    ```

5. Run the reportgenerator command to generate the HTML coverage report

    ``` bash
    reportgenerator -reports:./bolicheTests/lcov.info -targetdir:coveragereport -reporttypes:Html
    ```

6. It is also possible to run dotnet watch to rerun tests and generate coverage whenever a new change is detected to one of the project files

    ``` bash
    dotnet watch --project bolicheTests test /p:CollectCoverage=true /p:CoverletOutputFormat=lcov /p:CoverletOutput=./lcov.info
    ```


### Documentation

This project uses the following Commit Guidelines:

- build: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- ci: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
- docs: Documentation only changes
- feat: A new feature
- fix: A bug fix
- perf: A code change that improves performance
- refactor: A code change that neither fixes a bug nor adds a feature
- style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- test: Adding missing tests or correcting existing tests

---

## 📌 Support

Contact and support me through the following social medias:

- itch.io at [HypThaNyx](https://hypthanyx.itch.io/)
- Twitter at [@hypthanyx](https://twitter.com/hypthanyx)
- Instagram at [@hypthanyx](https://www.instagram.com/hypthanyx/)
- Linkedin at [Wesley Yago](https://www.linkedin.com/in/wesley-yago-da-silva/)
- Youtube at [HypThaNyx](https://www.youtube.com/channel/UC_x5u0TqJWN4O3GMwZRWkrg)

---

## 📝 License

<img alt="License" src="https://img.shields.io/badge/license-MIT-%2304D361">

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

🧰 Being developed by Wesley Yago!

# Um exemplo de SLAM em ROS <img src="https://lh3.googleusercontent.com/proxy/sQCSagzVuc1X3_zgLypJlEX_iDNLzb1urNU3lP54BJETeKExkKnuugvMpng6r_ULUjPqgUGKNjHDiqP78PxPzPPEm8maDXc0UOdgAxr-xg" width="40" />

## Visão geral

Este projeto descreve como simular um processo SLAM simples no ROS. Aqui, um robô segue um caminho predeterminado para sair de uma sala.
O robô faz uso de varredura a laser para identificar as paredes.

![SLAM no ROS](/slam_basic/rvi2.png "rvi2")

SLAM, sigla em inglês para Localização e Mapeamento Simultâneos, é uma técnica usada por robôs e carros autônomos para construir um mapa de um
ambiente ao mesmo tempo em que se localiza. No ROS, podemos fazer isso através do **RVIZ**, uma ferramenta que ajuda você a ver o que está acontecendo.

Este projeto é apenas um dos primeiros passos no maravilboso mundo do ROS.

## Arquivos

### Robô

O robô é um simples paralelepípedo com 3 rodas. Ele também possui um plugin para a varredura a laser hokuyo, para o SLAM. O primeiro_bot.urdf
é o arquivo que descreve esse bot.

### Launch

No arquivo launch, o rviz, o gazebo, o mundo, todos os nós são inicializados e o robô é colocado no mundo.
O arquivo que faz isso é bot_model.launch.

### Mundo

O mundo é o estágio em que a simulação opera. É carregado no gazebo. Nesse caso, o mundo carrega um terreno e uma estrutura
que é formado por 4 paredes com um pequeno espaço, é para onde o robô passa.

![Gazebo World](/slam_basic/gazebo_model.png "gazebo_model")

### Config

Os arquivos nesta pasta carregam os parâmetros básicos para o SLAM no rviz.

### Nós

Os ROS funcionam com nós. O mais importante é o nó /scan, que obtém o valor do scanner a laser, o /gmapping, que mapeia o local,
o /odom, que obtém os valores da pose, posição e orientação do robô. Os nós são descritos abaixo.

![Gazebo World](/slam_basic/rqt_graph.png "rqt_graph")

## Requisitos

  - ROS Melodic
  - Catkin
  - Rviz
  - Gazebo
  
## Construir

Você deve seguir no terminal:

- Criar o espaço de trabalho catkin:

``` sh
$ mkdir catkin_ws
$ cd catkin_ws
$ mkdir src
$ catkin_make
```

- Clonar o repositório e a construí-lo:

``` sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/marcos-moura97/slam_basic_ros.git
$ cd ..
$ catkin_make
```

## Para rodar

Para executar o projeto e ver o mundo do gazebo e o rviz, execute as seguintes etapas:



- Executar o roscore

``` sh
$ cd ~/catkin_ws/
$ source devel/setup.bash
$ roscore
```

- Lançar do programa

``` sh
$ roslaunch bot_model.launch
```

No RVIZ, selecione alguns nós, como mostra a imagem abaixo, e adicione um caminho a seguir com a ferramenta **2D Nav Goal** apontando para o local
que você deseja seguir.

![SLAM no ROS](/slam_basic/rviz1.png "rviz1")

## Mensagem final

Espero que isso ajude você a gostar da robótica tanto quanto eu :)

# A example of SLAM in ROS <img src="https://www.championprofessional.com/wp-content/uploads/2015/07/en-icon.png" width="40" />

## Overview

This project describes how to simulate a simple SLAM process in ROS. Here, a robot follow a predetermined path to get out of a room.
The robot makes use of laser scan to identify the walls.

![SLAM in ROS](/slam_basic/rvi2.png "rvi2")

SLAM, the acronym for Simultaneous Localization and Mapping, is a thecnique used by robots and autonomous cars to build a map of an 
environment at the same time that locate itself. In ROS we can do this through **RVIZ**, a tool that helps you to see what's going on.

This project is just one of the firsts steps into the ROS world.

## Files

### Robot

The robot is a simple parallelepiped with 3 wheels. It also has a plugin to the hokuyo laser scan, for the SLAM. The primeiro_bot.urdf 
is the file that describes this bot.

### Launch

In the launch file the rviz, the gazebo, the world, all the nodes are initialized and the robot is placed in the world. 
The file that make thhis is bot_model.launch.

### World

The world is the stage on which the simulation operates. It is loaded in gazebo. In this case, the world loads a ground and a structure
that is formed by 4 walls with a little gap, that's where the robot pass.

![Gazebo World](/slam_basic/gazebo_model.png "gazebo_model")

### Config

The files in this folder loads the basic parameters for the SLAM in rviz.

### Nodes

ROS work with nodes.The most important are the /scan node, that gets the value from the laser scaner, the /gmapping, that maps the place,
the /odom, that get the values of the pose, position and orientation, of the robot. The nodes are describes below.

![Gazebo World](/slam_basic/rqt_graph.png "rqt_graph")

## Dependencies

  - ROS Melodic
  - Catkin
  - Rviz
  - Gazebo
  
## To build

You must follow in terminal:

- Create the catkin workspace:

```sh
$ mkdir catkin_ws
$ cd catkin_ws
$ mkdir src
$ catkin_make
```

- Cloning the repository and building:

```sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/marcos-moura97/slam_basic_ros.git
$ cd ..
$ catkin_make
```

## To Run

To run the project and see the gazebo world and the rviz, execute the following steps:



- Running roscore

```sh
$ cd ~/catkin_ws/
$ source devel/setup.bash
$ roscore
```

- Launching the program

```sh
$ roslaunch bot_model.launch
```

In the RVIZ, select some nodes, as the image below shows, and add a path to follow with the tool **2D Nav Goal** pointing to the place
that you want to follow.

![SLAM in ROS](/slam_basic/rviz1.png "rviz1")

## Final message

I hope this helps you to enjoy robotics as much as I do :)


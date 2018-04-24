---
title: Instalar agentes y controladores de pruebas para Visual Studio | Microsoft Docs
ms.date: 03/02/2018
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bc5790ef520e86bf853cee6086bd6c8739cc23a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="install-test-agents-and-test-controllers"></a>Instalar agentes y controladores de pruebas

En el caso de escenarios de prueba en los que se utiliza Visual Studio y Visual Studio Team Services (VSTS) o Team Foundation Server (TFS), no se requiere un controlador de pruebas. Agents para Visual Studio controlan la orquestación comunicándose con VSTS o TFS. Podría darse un escenario en el que se ejecutan pruebas continuas para los flujos de trabajo de compilación y publicación en VSTS o TFS.

También considere la posibilidad de si mejor [usar Build o Release Management en lugar](use-build-or-rm-instead-of-lab-management.md) de Lab Management.

## <a name="system-requirements"></a>Requisitos del sistema

| Elemento | Requisitos |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 versión 2, Service Pack 1 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 versión 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Instalación del controlador de pruebas y agentes de prueba

Puede descargar agentes de Visual Studio 2017 desde [visualstudio.com](https://www.visualstudio.com/downloads/?q=agents). Desplácese hasta la parte inferior de la página y busque *Agents para Visual Studio 2017*. Seleccione *Agente* o *Controlador* y después elija *Descargar*. Ejecute el archivo ejecutable descargado para instalar el controlador o el agente de prueba.

Puede descargar agentes de Visual Studio 2015 y Visual Studio 2013 desde la página de [descargas anterior](https://www.visualstudio.com/vs/older-downloads/).

Estos instaladores están disponibles como archivos ISO para una instalación sencilla en máquinas virtuales.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versiones compatibles de TFS, Microsoft Test Manager, el controlador de pruebas y el agente de pruebas

Puede combinar diferentes versiones de TFS, Microsoft Test Manager (MTM), el controlador de pruebas y el agente de pruebas, según la tabla siguiente:

| TFS | MTM con el centro de laboratorio | Controlador | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: actualización desde la versión 2015 o instalación nueva | 2017 | 2017 | 2017 |
| 2017: actualización desde la versión 2015 o instalación nueva | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: actualización desde la versión 2015 o instalación nueva | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: actualización desde la versión 2013 | 2013 | 2013 |2013 |
| 2015: instalación nueva | 2013 | 2013 | 2013 |
| 2015: actualización desde la versión 2013 o instalación nueva | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Actualización desde agentes de prueba de Visual Studio 2013

Le recomendamos que use agentes de Visual Studio en todos los nuevos escenarios de pruebas automatizados. Puede usar la tarea *Implementar Test Agent* en una definición de compilación para descargar e instalar los agentes de pruebas en su equipo.

En la tabla siguiente se muestran los escenarios que se admiten en Agentes para Visual Studio 2013 y las alternativas para Team Foundation Server (TFS) 2015 y VSTS:

| Escenarios admitidos en Agentes para Visual Studio 2013 | Alternativa en TFS y VSTS |
| --- | --- |
| Flujos de trabajo de compilación-implementación-prueba en Visual Studio | Los usuarios pueden usar una [definición de compilación](/vsts/build-release/) (no una compilación XAML) para compilar, implementar y probar escenarios en TFS. |
| Pruebas de carga (pruebas de rendimiento) con máquinas remotas locales | Use Test Controller y Test Agents 2013 Update 5 para ejecutar pruebas de carga locales. |
| Ejecución remota de pruebas automatizadas desde Microsoft Test Manager con un entorno de laboratorio | Actualmente no existe alternativa para este escenario. Le recomendamos que use la tarea Ejecutar pruebas funcionales en definiciones de versión y compilación (no en una compilación XAML) para ejecutar pruebas de manera remota. |
| Desarrolladores ejecutando pruebas remotas en Visual Studio | Ya no se admite. |

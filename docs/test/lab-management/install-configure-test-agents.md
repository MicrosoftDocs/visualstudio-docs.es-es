---
title: Instalar agentes y controladores de pruebas
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27f030fb73629172e0b5a2d5d4cb27cf186bb69f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594271"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalar agentes y controladores de pruebas

En el caso de escenarios de prueba en los que se usa Visual Studio y Azure Test Plans o Team Foundation Server (TFS), no se requiere un controlador de pruebas. Agents para Visual Studio controla la orquestación al comunicarse con Azure Test Plans o TFS. Podría darse un escenario en el que se ejecutan pruebas continuas para los flujos de trabajo de compilación y publicación en Azure Test Plans o TFS.

También considere la posibilidad de si mejor [usar Build o Release Management en lugar](use-build-or-rm-instead-of-lab-management.md) de Lab Management.

## <a name="system-requirements"></a>Requisitos del sistema

En la siguiente tabla se muestran los requisitos del sistema para instalar el controlador de pruebas o el agente de pruebas para Visual Studio:

| Elemento | Requisitos |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016: Standard y Datacenter<br />Windows Server 2012 R2 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016: Standard y Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Instalación del controlador de pruebas y agentes de prueba

Puede descargar agentes de Visual Studio desde [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Busque *Agentes para Visual Studio 2019*, seleccione *Agente* o *Controlador* y elija *Descargar*. Ejecute el archivo ejecutable descargado para instalar el controlador o el agente de prueba.

Puede descargar agentes de Visual Studio 2017, Visual Studio 2015 y Visual Studio 2013 desde la página de [descargas anterior](https://visualstudio.microsoft.com/vs/older-downloads/).

Estos instaladores están disponibles como archivos ISO para una instalación sencilla en máquinas virtuales.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versiones compatibles de TFS, Microsoft Test Manager, el controlador de pruebas y el agente de pruebas

Puede combinar diferentes versiones de TFS, Microsoft Test Manager, el controlador de pruebas y el agente de pruebas, según la tabla siguiente:

| TFS | Microsoft Test Manager con Centro de laboratorio | Controlador | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: actualización desde la versión 2015 o instalación nueva | 2017 | 2017 | 2017 |
| 2017: actualización desde la versión 2015 o instalación nueva | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: actualización desde la versión 2015 o instalación nueva | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: actualización desde la versión 2013 | 2013 | 2013 |2013 |
| 2015: instalación nueva | 2013 | 2013 | 2013 |
| 2015: actualización desde la versión 2013 o instalación nueva | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Los escenarios de administración de laboratorio en TFS 2018 y Azure DevOps Services están en desuso. Para obtener más información, vea las [Notas de la versión de Team Foundation Server 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Actualización desde agentes de prueba de Visual Studio 2013

Le recomendamos que use agentes de Visual Studio en todos los nuevos escenarios de pruebas automatizados. Puede usar la tarea *Implementar Test Agent* en una canalización de compilación para descargar e instalar los agentes de pruebas en su equipo.

En la tabla siguiente se muestran los escenarios que se admiten en Agentes para Visual Studio 2013 y las alternativas para Team Foundation Server (TFS) 2015 y Azure Test Plans:

| Escenarios admitidos en Agentes para Visual Studio 2013 | Alternativa en TFS y Azure Test Plans |
| - | - |
| Flujos de trabajo de compilación-implementación-prueba en Visual Studio | Los usuarios pueden usar una [canalización de compilación](/azure/devops/pipelines/index?view=vsts) (no una compilación XAML) para compilar, implementar y probar escenarios en TFS. |
| Pruebas de carga (pruebas de rendimiento) con máquinas remotas locales | Use Test Controller y Test Agents 2013 Update 5 para ejecutar pruebas de carga locales. |
| Ejecución remota de pruebas automatizadas desde Microsoft Test Manager con un entorno de laboratorio | Actualmente no existe alternativa para este escenario. Le recomendamos que use la tarea Ejecutar pruebas funcionales en definiciones de versión y compilación (no en una compilación XAML) para ejecutar pruebas de manera remota. |
| Desarrolladores ejecutando pruebas remotas en Visual Studio | Ya no se admite. |

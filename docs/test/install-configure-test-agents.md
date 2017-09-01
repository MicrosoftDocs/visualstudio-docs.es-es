---
title: Instalar y configurar agentes de prueba | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
ms.assetid: EBAA2E04-A97A-4047-B739-8DBA7F2D5074
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 5d9aec436c00bc999356e402facf605c194c9d1a
ms.contentlocale: es-es
ms.lasthandoff: 06/02/2017

---
# <a name="install-and-configure-test-agents"></a>Instalar y configurar agentes de prueba

Para los escenarios de prueba que usan Visual Studio y Visual Studio Team Services o Team Foundation Server (TFS), no necesitará Test Controller porque los agentes de Microsoft Visual Studio controlan la orquestación comunicándose con Team Services o TFS. Por ejemplo, está ejecutando pruebas continuas con sus flujos de trabajo de versión y compilación en Team Services o TFS.

Si necesita que Test Controller o Test Agent funcionen con TFS 2013, use Agentes para Microsoft Visual Studio 2013 Update 5 y configure el controlador de pruebas.

También considere la posibilidad de si sería más sencillo [usar Build o Release Management en su lugar](lab-management/use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>¿Qué necesito?

**¿Dónde puedo obtener Test Controller y Test Agent?**

* Si está ejecutando pruebas con tareas de Build vNext y quiere instalar agentes desde un directorio local: 

  * [Descargar Agentes para Microsoft Visual Studio 2015 RTM y Update 1](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Descargar Agentes para Microsoft Visual Studio 2017 y Visual Studio 2015 Update 2](https://www.visualstudio.com/downloads/download-visual-studio-vs): pulse **Herramientas para Visual Studio 2015** y, después, seleccione **Agentes para Visual Studio 2015** desde la barra de navegación izquierda.

* [Descargue Agentes para Microsoft Visual Studio 2013 Update 5](http://go.microsoft.com/fwlink/p/?LinkId=619264), si quiere ejecutar:

  * Pruebas de carga con máquinas remotas locales.

  * Pruebas continuas de manera remota con Microsoft Test Manager o MSTest y opciones de prueba para entornos de laboratorio.

  * Pruebas continuas con TFS 2013.

Estos instaladores están disponibles como archivos ISO (CD virtual) para una instalación sencilla en máquinas virtuales. 

[¿Puedo mezclar versiones de TFS, Microsoft Test Manager, Test Controller y Test Agent?](#MixedVersions)

**¿Qué requisitos de sistema necesito para instalar Test Controller y Test Agent?**

| Elemento | Requisitos |
| ---- | ------------ |
| **Agent** | Windows 10 <br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 versión 2, Service Pack 1 |
| **Controller** | Windows 10 <br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 versión 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Preguntas y respuestas

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>P: ¿Puedo mezclar versiones de TFS, Microsoft Test Manager, Test Controller y Test Agent?

R: Sí, aquí se muestran las combinaciones compatibles:

| TFS | Microsoft Test Manager con Centro de laboratorio | Controlador | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: actualización desde la versión 2013 | 2013 | 2013 |2013 |
| 2015: instalación nueva | 2013 | 2013 | 2013 |
| 2015: actualización desde la versión 2013 o instalación nueva | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>P: ¿Test Agent 2015 será compatible con todos los escenarios que admiten Test Controller y Test Agent de Visual Studio 2013?

R: Le recomendamos que use Agentes para Visual Studio en todos los nuevos escenarios de pruebas automatizados. Puede usar la tarea Implementar Test Agent en una definición de compilación para descargar e instalar los agentes de pruebas en su equipo.
En la tabla siguiente se muestran los escenarios que se admiten en Agentes para Visual Studio 2013 y las alternativas para Team Foundation Server (TFS) 2015 y Team Services (TS).

| Escenarios admitidos en Agentes para Visual Studio 2013 | Alternativa en TFS y TS |
| --- | --- |
| Flujos de trabajo de compilación-implementación-prueba en Visual Studio | Los usuarios pueden usar una [definición de compilación](https://www.visualstudio.com/team-services/continuous-integration/) (no una compilación XAML) para compilar, implementar y probar escenarios en TFS. |
| Pruebas de carga (pruebas de rendimiento) con máquinas remotas locales | Use Test Controller/Test Agents 2013 Update 5 para ejecutar pruebas de carga locales. [Más información](https://msdn.microsoft.com/en-us/library/ff400223.aspx). |
| Ejecución remota de pruebas automatizadas desde Microsoft Test Manager con un entorno de laboratorio | Actualmente no existe alternativa para este escenario. Le recomendamos que use la tarea Ejecutar pruebas funcionales en definiciones de versión y compilación (no en una compilación XAML) para ejecutar pruebas de manera remota. |
| Desarrolladores ejecutando pruebas remotas en Visual Studio | Ya no se admite. |

<!-- ENDSECTION -->

## <a name="see-also"></a>Vea también

* [Configurar máquinas y recopilar información de diagnóstico con la configuración de pruebas](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)


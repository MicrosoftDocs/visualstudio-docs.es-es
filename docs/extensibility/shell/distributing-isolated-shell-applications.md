---
title: Distribuir aplicaciones de Shell aislado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6e9b7ded8d24e4d252d29338d89bd176648511a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="distributing-isolated-shell-applications"></a>Distribuir aplicaciones de Shell aislado
Debe instalar Visual Studio y el SDK de Visual Studio para crear una aplicación de shell aislado. Para distribuir la aplicación a los equipos de otros usuarios o los clientes, debe incluir un paquete redistribuible especial para el shell aislado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Requisitos previos para la distribución de aplicaciones de Shell aislado  
  
|nombre|Descripción|  
|----------|-----------------|  
|Visual Studio SDK|El SDK debe tener para desarrollar y probar las extensiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. También puede usar el SDK para crear su propia instancia del shell aislado de Visual Studio.<br /><br /> Visual Studio es un requisito previo para el SDK.|  
|Aislamiento de Microsoft Visual Studio Shell Redistributable|El paquete redistribuible de incluir en el programa de instalación cuando se compila en un entorno de herramientas en Visual Studio aislados de shell. El paquete redistribuible de Shell aislado incluye .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Crear un programa de instalación para la aplicación  
 Debe crear un programa de instalación especial para la aplicación de shell aislado o integrada. Para obtener más información, consulte [instalar una aplicación de Shell aislado](installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitir que las actualizaciones de la aplicación  
 El programa de instalación debe permitir la posibilidad de que se actualizará la aplicación, las actualizaciones de Microsoft o las actualizaciones de su empresa. Para obtener más información acerca de las actualizaciones, consulte [instrucciones de mantenimiento para las aplicaciones de Shell aislado](servicing-guidelines-for-isolated-shell-applications.md).
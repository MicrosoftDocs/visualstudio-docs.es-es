---
title: 'Cómo: agregar una dependencia a un paquete VSIX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697505"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Adición de una dependencia a un paquete VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede configurar una implementación de paquetes VSIX que instale las dependencias que no estén ya presentes en el equipo de destino. Para ello, incluya las dependencias de VSIX en el archivo source. Extension. vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para agregar una dependencia  
  
1. Abra el archivo source. Extension. vsixmanifest en la vista de **diseño** . Vaya a la pestaña **dependencias** y haga clic en **nuevo**.  
  
2. Para agregar una extensión instalada: en el cuadro de diálogo **Agregar nueva dependencia** , seleccione **extensión instalada** y, a continuación, para el **nombre**, seleccione una extensión de la lista.  
  
3. Para agregar otra VSIX que no está instalada:: en el cuadro de diálogo **Agregar nueva dependencia** , seleccione **archivo en el sistema de archivos** y, a continuación, use el botón **examinar** para seleccionar el VSIX.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del esquema de extensión VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

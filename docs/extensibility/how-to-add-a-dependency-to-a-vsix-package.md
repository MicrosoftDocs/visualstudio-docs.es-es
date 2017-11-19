---
title: "Cómo: agregar una dependencia a un paquete VSIX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Cómo: agregar una dependencia a un paquete VSIX
Puede configurar la implementación de un paquete VSIX que instala cualquier dependencia que ya no está presente en el equipo de destino. Para ello, incluya las dependencias VSIX en el archivo source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para agregar una dependencia  
  
1.  Abra el archivo source.extension.vsixmanifest en el **diseño** vista. Vaya a la **dependencias** ficha y haga clic en **nuevo**.  
  
2.  Para agregar una extensión instalada: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **extensión instalada** y, después, en la **nombre**, seleccione una extensión en la lista.  
  
3.  Para agregar otro VSIX que no está instalado:: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **archivo en el sistema de archivos** y, a continuación, use la **examinar** para seleccionar la extensión VSIX.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
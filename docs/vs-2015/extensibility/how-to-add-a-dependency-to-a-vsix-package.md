---
title: Filtrar Agregar una dependencia a un paquete VSIX | Documentos de Microsoft
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
ms.openlocfilehash: 97118134106614e1e04cd2bc328ad31480618116
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988668"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Filtrar Agregar una dependencia a un paquete VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede configurar una implementación de paquete VSIX que instala las dependencias que no están presentes en el equipo de destino. Para ello, incluyen las dependencias VSIX en el archivo source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para agregar una dependencia  
  
1.  Abra el archivo source.extension.vsixmanifest en el **diseño** vista. Vaya a la **dependencias** ficha y haga clic en **New**.  
  
2.  Para agregar una extensión instalada: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **extensión instalada** y, después, en el **nombre**, seleccione una extensión en la lista.  
  
3.  Para agregar otra extensión VSIX que no está instalado:: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **archivo en el sistema de archivos** y, a continuación, utilice el **examinar** botón para seleccionar el archivo VSIX.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparación de las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

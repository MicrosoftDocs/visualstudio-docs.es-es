---
title: 'Cómo: administrar una galería privada mediante la configuración del registro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204156"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Administración de una galería privada mediante la configuración del Registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si es un administrador o el desarrollador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas de la galería de Visual Studio, la galería de ejemplos o las galerías privadas. Para que una galería esté disponible o no disponible, cree un archivo. pkgdef que describa las claves del registro modificadas y sus valores.  
  
## <a name="managing-private-galleries"></a>Administrar galerías privadas  
 Puede crear un archivo. pkgdef para controlar el acceso a las galerías de varios equipos. Este archivo debe tener el formato siguiente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 La `Repositories` clave hace referencia a la galería para habilitarla o deshabilitarla. La galería de Visual Studio y la galería de ejemplos usan los siguientes GUID de repositorio:  
  
- Galería de Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galería de ejemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  El `Disabled` valor es opcional. De forma predeterminada, se habilita una galería.  
  
  El `Priority` valor determina el orden en el que las galerías aparecen en el cuadro de diálogo Opciones. La galería de Visual Studio tiene prioridad 10 y la galería de ejemplos tiene prioridad 20. Las galerías privadas comienzan con la prioridad 100. Si varias galerías tienen el mismo valor de prioridad, el orden en que aparecen viene determinado por los valores de sus atributos localizados `DisplayName` .  
  
  El `Protocol` valor es necesario para las galerías basadas en Atom o en SharePoint.  
  
  `DisplayName`Se debe especificar, o ambos, `DisplayNameResourceID` y `DisplayNamePackageGuid` . Si se especifica All, `DisplayNameResourceID` `DisplayNamePackageGuid` se usa el par y.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deshabilitar la galería de Visual Studio mediante un archivo. pkgdef  
 Puede deshabilitar una galería en un archivo. pkgdef. La siguiente entrada deshabilita la galería de Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La siguiente entrada deshabilita la galería de ejemplos:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Consulte también  
 [Galerías privadas](../extensibility/private-galleries.md)

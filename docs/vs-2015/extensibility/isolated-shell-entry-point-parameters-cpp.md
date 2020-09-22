---
title: Parámetros de punto de entrada de Shell aislado (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843143"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parámetros de punto de entrada de Shell aislado (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se inicia una aplicación basada en Shell de Visual Studio, llama al punto de entrada de inicio de Visual Studio Shell. La siguiente configuración se puede invalidar en la llamada al punto de entrada de inicio del shell. Para obtener una descripción de cada configuración, vea [. Archivos Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  La plantilla aislada de Visual Studio Shell crea un archivo de código fuente, *solutionName*. cpp, donde *solutionName* es el nombre de la solución para la aplicación. Este archivo define el punto de entrada principal de la aplicación, la _tWinMain función. Esta función invoca el punto de entrada de inicio del shell.  
  
  Puede cambiar el comportamiento de la aplicación cambiando esta configuración cuando se inicia la aplicación.  
  
## <a name="parameters"></a>Parámetros  
 El punto de entrada de inicio del shell de Visual Studio define cinco parámetros. No cambie los primeros cuatro parámetros. El quinto parámetro toma una lista de invalidaciones de configuración. Se llama al punto de entrada inicial del shell desde el punto de entrada principal de una aplicación.  
  
 El punto de entrada inicial del shell tiene la siguiente firma.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Si no desea invalidar ninguna configuración de aplicación, deje el valor del parámetro de invalidación de configuración como un puntero nulo.  
  
 Para reemplazar uno o más valores de configuración, pase una cadena Unicode que contenga la configuración que se va a reemplazar. La cadena es una lista separada por punto y coma de pares de nombre y valor. Cada par contiene el nombre de la configuración que se va a invalidar, seguido de un signo igual (=), seguido del valor que se va a aplicar a la configuración.  
  
> [!NOTE]
> No incluya espacios en blanco en las cadenas Unicode.  
  
 En el caso de valores booleanos, las cadenas siguientes representan el valor true; todas las demás cadenas representan el valor false. Estas cadenas no distinguen mayúsculas de minúsculas.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- sí  
  
## <a name="example"></a>Ejemplo  
 Para deshabilitar los complementos y cambiar la ubicación predeterminada de los proyectos de la aplicación, puede establecer el último parámetro en "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Consulte también  
 [Personalización del shell aislado](../extensibility/customizing-the-isolated-shell.md)   
 [Archivos .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

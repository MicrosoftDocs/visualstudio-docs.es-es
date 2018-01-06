---
redirect_url: shell/isolated-shell-entry-point-parameters-cpp
title: "Aislamiento de parámetros de punto de entrada de Shell (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5392188a75b474528df92be0c835b5c60dc2891
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parámetros de punto de entrada de Shell aislado (C++)
Cuando se inicia una aplicación basada en shell de Visual Studio, llama el punto de entrada de inicio del shell de Visual Studio. La siguiente configuración puede invalidarse en la llamada al punto de entrada de inicio del shell. Para obtener una descripción de cada configuración, vea [. Archivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   AppName  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 La plantilla de Visual Studio Shell aislado crea un archivo de código fuente, *nombresolución*.cpp, donde *solutionName* es el nombre de la solución para la aplicación. Este archivo define el punto de entrada principal para la aplicación, la función _tWinMain. Esta función invoca el punto de entrada de inicio del shell.  
  
 Puede cambiar el comportamiento de la aplicación cambiando estas opciones cuando se inicia la aplicación.  
  
## <a name="parameters"></a>Parámetros  
 El punto de entrada de inicio del shell de Visual Studio define cinco parámetros. No cambie los cuatro primeros parámetros. El quinto parámetro toma una lista de invalidación de la configuración. El punto de entrada de inicio del shell se llama desde el punto de entrada principal de una aplicación.  
  
 El punto de entrada de inicio del shell tiene la siguiente firma.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Si no desea reemplazar cualquier configuración de aplicación, deje el valor de la configuración de invalidar el parámetro como un puntero nulo.  
  
 Para reemplazar uno o más valores, pase una cadena Unicode que contiene los valores que se va a reemplazarse. La cadena es una lista separada por punto y coma de pares nombre / valor. Cada par contiene el nombre de la opción para invalidar, seguido por un signo igual (=), seguido del valor que se aplicará a la configuración.  
  
> [!NOTE]
>  No incluya espacios en blanco en las cadenas de Unicode.  
  
 Para valores booleanos, las cadenas siguientes representan el valor true; todas las demás cadenas representan el valor false. Estas cadenas distinguen mayúsculas de minúsculas.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   el  
  
-   true  
  
-   sí  
  
## <a name="example"></a>Ejemplo  
 Para deshabilitar complementos y cambiar la ubicación de proyectos predeterminada para la aplicación, puede establecer el último parámetro para "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el Shell aislado](../extensibility/customizing-the-isolated-shell.md)   
 [. Pkgdef archivos](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
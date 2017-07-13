---
title: "Administrar los recursos de la aplicación (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 5cb2e044f5c55881adade6d3022fc453360a2e9c
ms.contentlocale: es-es
ms.lasthandoff: 05/30/2017

---
# Administrar los recursos de la aplicación (.NET)
<a id="managing-application-resources-net" class="xliff"></a>
Los archivos de recursos son archivos que forman parte de una aplicación, pero no se compilan. Un ejemplo de estos archivos son los  archivos de icono de ejemplo o los archivos de audio. Puesto que estos archivos no forman parte del proceso de compilación, se pueden cambiar sin tener que volver a compilar los archivos binarios. Si piensa localizar la aplicación, debe usar los archivos de recursos para todas las cadenas y los demás recursos que deben cambiarse al localizar la aplicación.  
  
 Para obtener más información sobre los recursos de aplicaciones de escritorio .NET, vea [Recursos de aplicaciones de escritorio](/dotnet/framework/resources/index). Para más información sobre los recursos de aplicaciones de escritorio C++, vea [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
 Las aplicaciones de la Tienda Windows usan un modelo de recursos distinto al de las aplicaciones de escritorio. Para obtener información sobre los recursos de las aplicaciones de la Tienda Windows, vea [Definición de recursos de aplicaciones](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) en el sitio web del Centro de desarrollo de Windows.  
  
## Trabajar con recursos
<a id="working-with-resources" class="xliff"></a>  
 En un proyecto de código administrado, abra la ventana de propiedades del proyecto (haga clic en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Propiedades**o escriba las **propiedades del proyecto** en la ventana **Inicio rápido** , o bien presione ALT + ENTRAR en la ventana **Explorador de soluciones** ). Seleccione la pestaña **Recursos** . Puede agregar un archivo .resx si el proyecto no contiene uno ya y, a continuación, agregar y eliminar diferentes tipos de recursos y modificar los recursos existentes.  
  
 Para obtener información sobre cómo trabajar con recursos en proyectos de C++, vea [How to: Create a Resource](/cpp/windows/how-to-create-a-resource) (Cómo: Crear un recurso).

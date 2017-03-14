---
title: Administrar herramientas externas | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: c36d97b83aa0892235c8f196cf6af63520b3547c
ms.openlocfilehash: a31b90643e3707348595fce02ec37a1c02a97195
ms.lasthandoff: 03/01/2017

---
# <a name="manage-external-tools"></a>Administrar herramientas externas
Se puede llamar a herramientas externas desde Visual Studio mediante el menú **Herramientas**. Algunas herramientas predeterminadas están disponibles en el menú **Herramientas**, pero se pueden agregar otros archivos ejecutables propios.  

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Herramientas disponibles en el menú Herramientas de Visual Studio
 El **Herramientas** menú contiene varios comandos integrados, como:

*  **Extensiones y actualizaciones ** para [administrar Extensiones de Visual Studio](finding-and-using-visual-studio-extensions.md)
*  **Administrador de fragmentos de código... ** para [organizar fragmentos de código](code-snippets.md#code-snippet-manager)
*  **PreEmptive Protection - Dotfuscator** para iniciar [Dotfuscator Community Edition (CE)](dotfuscator/index.md) si está [instalado](dotfuscator/install.md)
*  **Personalizar...** para personalizar [menús y barras de herramientas](how-to-customize-menus-and-toolbars-in-visual-studio)
*  **Opciones... ** para [establecer numerosas opciones diferentes para el IDE de Visual Studio y otras herramientas](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Agregar nuevas herramientas al menú Herramientas 
 Puede agregar una herramienta externa al menú **Herramientas**. Abra el cuadro de diálogo **Herramientas externas..**, haga clic en **Agregar** y rellene la información. Por ejemplo, la entrada siguiente hace que el Explorador de Windows se abra en el directorio del archivo que tiene abierto actualmente en Visual Studio:  
  
1.  Título: *Abrir ubicación del archivo*
  
2.  Comando: `explorer.exe`  
  
3.  Argumentos: `/root, "$(ItemDir)"`  
  
 La siguiente es una lista completa de los argumentos que se pueden utilizar al definir una herramienta externa.
  
> [!NOTE]
>  La barra de estado del IDE muestra las variables Línea actual y Columna actual para indicar dónde se encuentra el punto de inserción en el Editor de código activo. La variable Texto actual devuelve el texto o el código seleccionado en dicha ubicación.  
  
|Nombre|Argumento|Descripción|  
|----------|--------------|-----------------|  
|Ruta de acceso del elemento|$(ItemPath)|Nombre de archivo completo del archivo actual (unidad + ruta de acceso + nombre de archivo).|  
|Directorio del elemento|$(ItemDir)|Directorio del archivo actual (unidad + ruta de acceso).|  
|Nombre de archivo del elemento|$(ItemFilename)|Nombre de archivo del archivo actual (nombre de archivo).|  
|Extensión del elemento|$(ItemExt)|Extensión del nombre de archivo del archivo actual.|  
|Línea actual|$(CurLine)|Posición de línea actual del cursor en la ventana de código.|  
|Columna actual|$(CurCol)|Posición de columna actual del cursor en la ventana de código.|  
|Texto actual|$(CurText)|Texto seleccionado.|  
|Ruta de acceso de destino|$(TargetPath)|Nombre de archivo completo del elemento que se va a compilar (unidad + ruta de acceso + nombre de archivo).|  
|Directorio de destino|$(TargetDir)|Directorio del elemento que se va a compilar.|  
|Nombre de destino|$(TargetName)|Nombre de archivo del elemento que se va a compilar.|  
|Extensión de destino|$(TargetExt)|Extensión del nombre de archivo del elemento que se va a compilar.|  
|Directorio binario|$(BinDir)|Ubicación final del archivo binario que se va a compilar (definida como unidad + ruta de acceso). Por ejemplo:**\\...\Mis documentos\Visual Studio \<Versión>\\<NombreDeProyecto\>\bin\debug**|  
|Directorio del proyecto|$(ProjDir)|Directorio del proyecto actual (unidad + ruta de acceso).|  
|Nombre de archivo del proyecto|$(ProjFileName)|Nombre de archivo del proyecto actual (unidad + ruta de acceso + nombre de archivo).|  
|Directorio de la solución|$(SolutionDir)|Directorio de la solución actual (unidad + ruta de acceso).|  
|Nombre de archivo de la solución|$(SolutionFileName)|Nombre de archivo de la solución actual (unidad + ruta de acceso + nombre de archivo).|  

## <a name="see-also"></a>Vea también  
 [Herramientas de compilación de C/C++](/visual-cpp/build/reference/c-cpp-build-tools)


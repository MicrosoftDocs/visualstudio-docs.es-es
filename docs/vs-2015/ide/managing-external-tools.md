---
title: Administración de herramientas externas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6dec053e1075865b51c14df951915308852f8a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445426"
---
# <a name="managing-external-tools"></a>Administrar herramientas externas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede llamar a herramientas externas desde Visual Studio. Algunas herramientas predeterminadas están disponibles en el menú **Herramientas**, pero se pueden agregar otros archivos ejecutables propios.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Herramientas disponibles en el menú Herramientas de Visual Studio  
 Puede llamar a las herramientas siguientes desde el menú **Herramientas** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. También puede llamarlas por su nombre desde la ventana **Inicio rápido**. Por ejemplo, para llamar a GuidGen.exe, escriba **Crear GUID**.  
  
1. Crear GUID: genera un GUID.  
  
2. Búsqueda de errores: obtiene un mensaje de error del valor especificado. Para obtener más información, consulte [Referencia de ERRLOOK](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).  
  
3. Herramienta de seguimiento de ATL/MFC: muestra mensajes de seguimiento de depuración en los orígenes ATL y MFC.  
  
4. PreEmptive Protection - Dotfuscator: Protege los programas de .NET frente a ingeniería inversa.  
  
5. SPY ++: Muestra gráficamente los procesos, subprocesos, windows y los mensajes de ventana.  
  
6. Editor de configuración del servicio WCF: Permite crear y modificar la configuración para los servicios WCF.  
  
> [!WARNING]
> Puede que aparezca una lista diferente de herramientas externas, según la edición de Visual Studio que tenga instalada y el perfil de configuración que haya aplicado. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="adding-new-tools"></a>Agregar nuevas herramientas  
 Puede agregar una herramienta externa al menú **Herramientas**. Abra el cuadro de diálogo **Herramientas externas**, haga clic en **Agregar** y rellene la información. Por ejemplo, la entrada siguiente hace que el Explorador de Windows se abra en el directorio del archivo que tiene abierto actualmente en Visual Studio:  
  
1. Título: Abrir ubicación del archivo  
  
2. Comando: explorer.exe  
  
3. Argumentos: /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Argumentos para herramientas externas  
 Los siguientes argumentos son variables de Visual Studio que se asignan cuando se inicia una herramienta externa. Puede ver una lista de vínculos a herramientas externas, como el Bloc de notas o Spy++, en el menú **Herramientas**, mediante el cuadro de diálogo Herramientas externas.  
  
> [!NOTE]
> La barra de estado del IDE muestra las variables Línea actual y Columna actual para indicar dónde se encuentra el punto de inserción en el Editor de código activo. La variable Texto actual devuelve el texto o el código seleccionado en dicha ubicación.  
  
|Name|Argumento|Descripción|  
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
 [Herramientas de compilación de C/C++](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)

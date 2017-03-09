---
title: "Administrar herramientas externas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools"
helpviewer_keywords: 
  - "contenedor de pruebas de controles ActiveX"
  - "Herramienta de seguimiento de ATL"
  - "ATLTraceTool.exe"
  - "herramienta de enlace"
  - "herramienta de creación de GUID"
  - "DisableMsg (herramienta)"
  - "ErrLook (herramienta)"
  - "herramienta de búsqueda de errores"
  - "herramientas externas [Visual Studio]"
  - "GUIDGEN (herramienta)"
  - "HCW (Help Workshop)"
  - "Help Workshop"
  - "compilador de IDL"
  - "Local Test Manager"
  - "LTM (Local Test Manager)"
  - "MAKEHM (herramienta)"
  - "mc (Message Compiler)"
  - "Message Compiler [Visual Studio]"
  - "MIDL, herramientas externas"
  - "Midlc (IDL Compiler)"
  - "MkTypLib (herramienta)"
  - "ODBC Test"
  - "Odbcte32.exe"
  - "Odbcte32.exe"
  - "OLE DB Rowset Viewer"
  - "visor de objetos OLE/COM"
  - "OLEVIEW (visor de objetos)"
  - "RC (Compilador de recursos)"
  - "ReBase (herramienta)"
  - "compilador de recursos"
  - "RowsetViewer (herramienta)"
  - "herramientas [Visual Studio], externos"
  - "tstcon32.exe"
  - "Type Library Generator"
  - "undname.exe"
  - "utilidades, herramientas externas"
  - "UUID Generator"
  - "Uuidgen.exe"
  - "Vcspawn.exe"
  - "Vsvars32.bat"
  - "WebDbg (herramienta)"
  - "Windows NT C++ Symbol Undecorator"
  - "Enlazador de imágenes de Windows NT"
  - "Windows NT Image Rebaser"
  - "Windows NT Message Compiler"
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
caps.handback.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Administrar herramientas externas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede llamar a herramientas externas desde Visual Studio.  Algunas herramientas predeterminadas están disponibles en el menú **Herramientas**, pero se pueden agregar otros archivos ejecutables propios.  
  
## Herramientas disponibles en el menú Herramientas de Visual Studio  
 Puede llamar a las herramientas siguientes desde el menú **Herramientas** en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  También puede llamarlas por su nombre desde la ventana **Inicio rápido**.  Por ejemplo, para llamar a GuidGen.exe, escriba Crear GUID.  
  
1.  Crear GUID: genera un GUID.  
  
2.  Búsqueda de errores: obtiene un mensaje de error del valor especificado.  Para obtener más información, consulte [Referencia de ERRLOOK](/visual-cpp/build/reference/errlook-reference).  
  
3.  Herramienta de seguimiento de ATL\/MFC: muestra mensajes de seguimiento de depuración en los orígenes ATL y MFC.  
  
4.  Dotfuscator y Analytics de PreEmptive: protege los programas de .NET frente a técnicas de ingeniería inversa.  
  
5.  SPY\+\+: muestra procesos, subprocesos, ventanas y mensajes de ventana de forma gráfica.  
  
6.  Editor de configuración de servicios WCF: permite crear y modificar opciones de configuración para servicios WCF.  
  
> [!WARNING]
>  Puede que aparezca una lista diferente de herramientas externas, según la edición de Visual Studio que tenga instalada y el perfil de configuración que haya aplicado.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Agregar nuevas herramientas  
 Es posible agregar una herramienta externa al menú **Herramientas**.  Abra el cuadro de diálogo **Herramientas externas**, haga clic en **Agregar** y rellene la información.  Por ejemplo, la entrada siguiente hace que el Explorador de Windows se abra en el directorio del archivo que tiene abierto actualmente en Visual Studio:  
  
1.  Título: Abrir ubicación del archivo  
  
2.  Comando: explorer.exe  
  
3.  Argumentos: \/root, "$\(ItemDir\)"  
  
## Argumentos para herramientas externas  
 Los siguientes argumentos son variables de Visual Studio que se asignan cuando se inicia una herramienta externa.  Puede ver una lista de vínculos a herramientas externas, como el Bloc de notas o Spy\+\+, en el menú **Herramientas**, mediante el cuadro de diálogo Herramientas externas.  
  
> [!NOTE]
>  La barra de estado del IDE muestra las variables Línea actual y Columna actual para indicar dónde se encuentra el punto de inserción en el Editor de código activo.  La variable Texto actual devuelve el texto o el código seleccionado en dicha ubicación.  
  
|Nombre|Argumento|Descripción|  
|------------|---------------|-----------------|  
|Ruta de acceso del elemento|$\(ItemPath\)|Nombre de archivo completo del archivo actual \(unidad \+ ruta de acceso \+ nombre de archivo\).|  
|Directorio del elemento|$\(ItemDir\)|Directorio del archivo actual \(unidad \+ ruta de acceso\).|  
|Nombre de archivo del elemento|$\(ItemFilename\)|Nombre de archivo del archivo actual \(nombre de archivo\).|  
|Extensión del elemento|$\(ItemExt\)|Extensión del nombre de archivo del archivo actual.|  
|Línea actual|$\(CurLine\)|Posición de línea actual del cursor en la ventana de código.|  
|Columna actual|$\(CurCol\)|Posición de columna actual del cursor en la ventana de código.|  
|Texto actual|$\(CurText\)|Texto seleccionado.|  
|Ruta de acceso de destino|$\(TargetPath\)|Nombre de archivo completo del elemento que se va a compilar \(unidad \+ ruta de acceso \+ nombre de archivo\).|  
|Directorio de destino|$\(TargetDir\)|Directorio del elemento que se va a compilar.|  
|Nombre de destino|$\(TargetName\)|Nombre de archivo del elemento que se va a compilar.|  
|Extensión de destino|$\(TargetExt\)|Extensión del nombre de archivo del elemento que se va a compilar.|  
|Directorio binario|$\(BinDir\)|Ubicación final del archivo binario que se va a compilar \(definida como unidad \+ ruta de acceso\).  Por ejemplo:\\...\\Mis documentos\\Visual Studio \<Versión\>\\\<NombreDeProyecto\>\\bin\\debug|  
|Directorio del proyecto|$\(ProjDir\)|Directorio del proyecto actual \(unidad \+ ruta de acceso\).|  
|Nombre de archivo del proyecto|$\(ProjFileName\)|Nombre de archivo del proyecto actual \(unidad \+ ruta de acceso \+ nombre de archivo\).|  
|Directorio de la solución|$\(SolutionDir\)|Directorio de la solución actual \(unidad \+ ruta de acceso\).|  
|Nombre de archivo de la solución|$\(SolutionFileName\)|Nombre de archivo de la solución actual \(unidad \+ ruta de acceso \+ nombre de archivo\).|  
  
## Vea también  
 [Herramientas de compilación de C\/C\+\+](/visual-cpp/build/reference/c-cpp-build-tools)
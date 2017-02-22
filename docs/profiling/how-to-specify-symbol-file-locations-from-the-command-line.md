---
title: "C&#243;mo: Especificar ubicaciones del archivo de s&#237;mbolos desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Especificar ubicaciones del archivo de s&#237;mbolos desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para mostrar información de símbolos como nombres de función y números de línea, la herramienta de línea de comandos VSPerfReport requiere acceso a los archivos de símbolos \(.PDB\) de los componentes para los que se generan perfiles y a los archivos de sistema de Windows.  Los archivos de símbolos se crean cuando se compila un componente.  Para obtener más información, vea [VSPerfReport](../profiling/vsperfreport.md).  VSPerfReport busca automáticamente los archivos de símbolos en las ubicaciones siguientes:  
  
-   Rutas de acceso especificadas en la opción **\/SymbolPath** o en la variable de entorno **\_NT\_SYMBOL\_PATH**.  
  
-   Ruta de acceso local exacta donde se compiló un componente.  
  
-   Directorio que contiene el archivo de datos de generación de perfiles \(.vsp o .vsps\).  
  
 Microsoft proporciona los archivos .pdb para muchos de sus productos en línea en un servidor de símbolos.  Si el equipo que utiliza para los informes está conectado a Internet, VSPerfReport se conecta al servidor de símbolos en línea para buscar automáticamente información del símbolo y guarda los archivos en un almacén local.  
  
 Puede especificar la ubicación de los archivos de símbolos y del almacén del servidor de símbolos de Microsoft de las maneras siguientes:  
  
-   Establezca la variable de entorno **\_NT\_SYMBOL\_PATH**.  
  
-   Agregue la opción **\/SymbolPath** a la línea de comandos de VSPerfReport.  
  
 También puede utilizar ambos métodos.  
  
> [!NOTE]
>  Si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se instala en el equipo local, posiblemente ya se ha especificado una ubicación para los archivos de símbolos de Windows.  Para obtener más información, vea [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md).  Todavía se debe configurar VSPerfReport para utilizar la ubicación y el servidor como se describe más adelante en este tema.  
  
## Especificar archivos de símbolos de Windows  
  
#### Para configurar el uso del servidor de símbolos de Windows  
  
1.  Si es necesario, cree un directorio para almacenar los archivos de símbolos localmente.  
  
2.  Utilice la sintaxis siguiente para establecer la variable de entorno **\_NT\_SYMBOL\_PATH** o la opción \/SymbolPath de VSPerfReport:  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     donde es la ruta *LocalStore* de directorio local que creó.  
  
## Especificar archivos de símbolos de componentes  
 Las herramientas de generación de perfiles buscan los archivos .pdb de los componentes para los que desea generar perfiles en sus ubicaciones originales que están almacenadas en los componentes o en la carpeta que contiene el archivo de datos de generación de perfiles.  Puede especificar otras ubicaciones donde buscar si agrega una o más rutas de acceso a **\_NT\_SYMBOL\_PATH** o a la opción **\/SymbolPath**.  Separe las rutas de acceso con puntos y coma.  
  
## Ejemplo  
 La siguiente línea de comandos establece la variable de entorno **\_NT\_SYMBOL\_PATH** en el servidor de símbolos de Windows y el directorio local en **C:\\Symbols**.  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 La siguiente línea de comandos de VSPerfReport agrega el directorio C:\\Projects\\Symbols a la ruta de búsqueda con la opción **\/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**
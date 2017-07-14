---
title: "Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
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
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 237acc5cc58646bc9f4e1ab6d2fbe976bb7ac124
ms.contentlocale: es-es
ms.lasthandoff: 07/14/2017

---
# Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos
<a id="how-to-specify-symbol-file-locations-from-the-command-line" class="xliff"></a>
Para mostrar información de símbolos como nombres de función y números de línea, la herramienta de línea de comandos VSPerfReport requiere acceso a los archivos de símbolos (.pdb) de los componentes que generan perfiles y los archivos de sistema de Windows. Los archivos de símbolos se crean cuando se compila un componente. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport busca archivos de símbolos automáticamente en las siguientes ubicaciones:  
  
-   Las rutas de acceso especificadas en la opción **/SymbolPath** o en la variable de entorno **_NT_SYMBOL_PATH**.  
  
-   La ruta local exacta donde se compiló un componente.  
  
-   El directorio que contiene el archivo de datos de generación de perfiles (.vsp o .vsps).  
  
 Microsoft proporciona los archivos .pdb para muchos de sus productos en línea en un servidor de símbolos. Si el equipo que está usando para los informes está conectado a Internet, VSPerfReport se conecta al servidor de símbolos en línea para buscar información de símbolos automáticamente y guardar los archivos en un almacén local.  
  
 Puede especificar la ubicación de los archivos de símbolos y el almacén de servidor de símbolos de Microsoft de las siguientes formas:  
  
-   Establezca la variable de entorno **_NT_SYMBOL_PATH**.  
  
-   Agregue la opción **/SymbolPath** a la línea de comandos de VSPerfReport.  
  
 También puede utilizar ambos métodos.  
  
> [!NOTE]
>  Si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalado en el equipo local, probablemente ya se ha especificado una ubicación de los archivos de símbolos de Windows. Para obtener más información, consulte [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md). Todavía debe configurar VSPerfReport para utilizar la ubicación y el servidor tal como se describe más adelante en este tema.  
  
## Especificar archivos de símbolos de Windows
<a id="specifying-windows-symbol-files" class="xliff"></a>  
  
#### Para configurar el uso del servidor de símbolos de Windows
<a id="to-configure-the-use-of-the-windows-symbol-server" class="xliff"></a>  
  
1.  Si es necesario, cree un directorio para almacenar localmente los archivos de símbolos.  
  
2.  Use la siguiente sintaxis para establecer la variable de entorno **_NT_SYMBOL_PATH** o la opción VSPerfReport /SymbolPath:  
  
     **srv\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
     donde *LocalStore* es la ruta de acceso del directorio local que creó.  
  
## Especificar archivos de símbolos de componente
<a id="specifying-component-symbol-files" class="xliff"></a>  
 Las herramientas de generación de perfiles buscan los archivos .pdb de los componentes de los cuales desea generar perfiles en sus ubicaciones originales que se almacenan en los componentes o en la carpeta que contiene el archivo de datos de generación de perfiles. Puede especificar otras ubicaciones de búsqueda mediante la adición de una o más rutas de acceso a **_NT_SYMBOL_PATH** o a la opción **/SymbolPath**. Separe las rutas de acceso con punto y coma.  
  
## Ejemplo
<a id="example" class="xliff"></a>  
 La siguiente línea de comandos establece la variable de entorno **_NT_SYMBOL_PATH** para el servidor de símbolos de Windows y el directorio local a **C:\Symbols**.  
  
 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 La siguiente línea de comandos de VSPerfReport agrega el directorio C:\Projects\Symbols a la ruta de búsqueda mediante la opción **/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**

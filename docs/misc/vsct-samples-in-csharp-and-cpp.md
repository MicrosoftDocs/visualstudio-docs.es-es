---
title: "Ejemplos de VSCT en C# y C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivos de VSCT, ejemplos"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# Ejemplos de VSCT en C# y C++
VSCT se ha convertido en la nueva forma de definir comandos.  Debido a esto, un cambio ha producido en cómo los ejemplos de VSCT son compilados en C\# y C\+\+.  Los comandos se definen ahora en C\+\+ con archivos externos y en C\# a una sección de Símbolos en el archivo de .vsct.  
  
## definición de comandos  
  
### archivos externos de C\+\+  
 En los ejemplos de C\+\+, el compilador de VSCT incluye archivos externos para definir las constantes utilizadas en las definiciones de los comandos.  La manera de incluir estos archivos y de esta manera de definir constantes en las definiciones de los comandos es agregar una etiqueta de `Extern` dentro del archivo de .vsct y especificar el nombre de las referencias a archivos externos dentro del atributo de `href` .  estos archivos son:  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 El siguiente fragmento del archivo de c\+\+. .vsct muestra cómo incluir estos archivos:  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### símbolos de C\#  
 En los ejemplos de C\#, el archivo de .vsct tiene una sección en el propio archivo de `Symbols` para definir comandos.  La definición de símbolos en un archivo de .vsct en C\# proviene la manera en que los id. de los elementos son definidas por la tabla de comandos.  A continuación se muestra un fragmento de un archivo de C\# .vsct que especifique comandos y constantes asociado a ellas:  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## Mapas de bits de incrustación  
  
### C\#  
 Los mapas de bits en los binarios de C\# y C\+\+ CTO se almacenan externamente en el disco.  El id. bitmap se define de forma de modo que la definición debe proporcionar un atributo del GUID para el mapa de bits, un atributo de `resID` de spline bitmap que contiene los mapas de bits y, a continuación los id. numéricos de los elementos utilizados dentro de una definición de botón \(atributo de`usedList` \).  Un aspecto importante de esta declaración es que el id. de elemento debe ser el índice real \(basado en uno\) del interior del mapa de bits la curva spline bitmap.  
  
 En el ejemplo siguiente una curva spline bitmap se incluye que contiene un solo elemento.  El identificador de este elemento se define como guidMenuAndCommandsCmdSet: el bmpArrow, por lo que el bmpArrow deben definirse como 1.  También es la declaración del mapa de bits.  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
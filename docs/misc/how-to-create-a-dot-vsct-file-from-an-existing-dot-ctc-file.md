---
title: "C&#243;mo: Crear un archivo .Vsct a partir de un archivo .Ctc existente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivos VSCT, creación basada en un archivo .ctc"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# C&#243;mo: Crear un archivo .Vsct a partir de un archivo .Ctc existente
Puede crear un archivo de vsct basado en XML de un archivo de origen de comando tabla .ctc existente. Al hacerlo, puede aprovechar las ventajas del nuevo basado formato del compilador de la tabla de comandos \(VSCT\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Para crear un archivo .vsct a partir de un archivo .ctc existente  
  
1.  Obtenga una copia del lenguaje Perl.  
  
2.  Obtenga una copia de la secuencia de comandos Perl ConvertCTCToVSCT.pl, que normalmente se encuentra en la carpeta *\<ruta de acceso de instalación del SDK de Visual Studio SDK\>*\\VisualStudioIntegration\\Tools\\bin.  
  
3.  Obtenga una copia del archivo .ctc de origen que desea va a convertir.  
  
4.  Coloque los archivos en el mismo directorio.  
  
5.  En la ventana del símbolo del sistema de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], navegue hasta el directorio.  
  
6.  Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     donde PkgCmd.ctc es el nombre del archivo .ctc y PkgCmd.vsct es el nombre del archivo vsct que desea crear.  
  
     Esto crea un nuevo archivo de origen de tabla de comandos XML .vsct. Puede compilar el archivo usando el archivo Vsct.exe, el compilador VSCT, tal como lo haría con cualquier otro archivo .vsct.  
  
    > [!NOTE]
    >  Puede mejorar la legibilidad del archivo .vsct volviendo a asignar formato a los comentarios XML.  
  
## Vea también  
 [Cómo: crear una. Archivo de Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
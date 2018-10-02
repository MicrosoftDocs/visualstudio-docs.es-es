---
title: 'Cómo: crear una. Archivo de Vsct desde una existente. Archivos de CTC | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0d267e6046539001cbe454ab69867c02f0a606ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579499"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Cómo: Crear un archivo .Vsct a partir de un archivo .Ctc existente
Puede crear un archivo de vsct basado en XML de un archivo de origen de comando tabla .ctc existente. Al hacerlo, puede sacar partido del nuevo basado en XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] formato del compilador de comandos (VSCT) de la tabla.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para crear un archivo .vsct a partir de un archivo .ctc existente  
  
1.  Obtenga una copia del lenguaje Perl.  
  
2.  Obtenga una copia de la secuencia de comandos Perl ConvertCTCToVSCT.pl, que normalmente se encuentra en la  *\<ruta de instalación de Visual Studio SDK >* carpeta \VisualStudioIntegration\Tools\bin.  
  
3.  Obtenga una copia del archivo .ctc de origen que desea va a convertir.  
  
4.  Coloque los archivos en el mismo directorio.  
  
5.  En el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ventana del símbolo de comandos, navegue hasta el directorio.  
  
6.  Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     donde PkgCmd.ctc es el nombre del archivo .ctc y PkgCmd.vsct es el nombre del archivo vsct que desea crear.  
  
     Esto crea un nuevo archivo de origen de tabla de comandos XML .vsct. Puede compilar el archivo usando el archivo Vsct.exe, el compilador VSCT, tal como lo haría con cualquier otro archivo .vsct.  
  
    > [!NOTE]
    >  Puede mejorar la legibilidad del archivo .vsct volviendo a asignar formato a los comentarios XML.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear una. Archivo de Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
---
title: Modificar el Shell aislado mediante el. Archivo Pkgundef | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f863377f326dd7bd62381a34c6236d938b11505
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificar el Shell aislado mediante el. Archivo Pkgundef
Puede modificar el archivo .pkgundef para excluir las entradas del registro especificada de una aplicación de shell aislado. Normalmente, la primera vez que se inicie una aplicación en un equipo, el shell de Visual Studio copia las entradas de registro existentes de Visual Studio a la clave del registro raíz para la aplicación. Esto incluye todas las referencias a VSPackages instaladas actualmente.  
  
 Para excluir una entrada del Registro específica de una aplicación de shell aislado, agregue al archivo de .pkgundef aplicación seguida de la clave de paquete con la entrada. Las claves y entradas se representan como en el archivo .pkgdef; es decir, como [$RootKey$] o [$RootKey$\\*subclave*] y "*entrada*" =*valor*, donde *subclave* es la subclave para influir, *entrada* es la entrada que se va a quitar, y *valor* sea `""` o `dword:00000000`.  
  
 Para excluir varias entradas de una clave del registro, se trata de enumerar la clave una vez, seguido de una línea para cada entrada que se va a excluir.  
  
 Para excluir una clave del registro completo de una aplicación de shell aislado, agregue la clave en el archivo de aplicación .pkgundef pero no especifica ninguna entrada del registro para esa clave.  
  
 Puede agregar comentarios al archivo .pkgundef. Una sola línea de comentario debe tener dos barras diagonales como los dos primeros caracteres.  
  
 Por ejemplo, para quitar el **conectar con base de datos** y **conectar a Serve r** comandos en el **herramientas** menú, puede elimine la línea:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 y agregue la línea:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 archivo .pkgundef de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [GUID de paquete de características de Visual Studio](package-guids-of-visual-studio-features.md)   
 [Personalización del Shell aislado](customizing-the-isolated-shell.md)
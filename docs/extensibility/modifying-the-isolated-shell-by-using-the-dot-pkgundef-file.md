---
title: Modificar el Shell aislado mediante el. Archivo Pkgundef | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificar el Shell aislado mediante el. Archivo Pkgundef
Puede modificar el archivo .pkgundef para excluir las entradas del registro especificado de una aplicación de shell aislado. Normalmente, la primera vez que se inicie una aplicación en un equipo, el shell de Visual Studio copia las entradas del registro de Visual Studio existentes en la clave del registro raíz para la aplicación. Esto incluye todas las referencias a VSPackages instalada actualmente.  
  
 Para excluir una entrada del Registro específica de una aplicación de shell aislado, agregue el archivo .pkgundef la aplicación la clave de paquete seguida de la entrada. Las claves y entradas se representan como en el archivo .pkgdef; es decir, como [$RootKey$] o [$ $RootKey\\*subclave*] y "*entrada*" =*valor*, donde *subclave* es la subclave afectar *entrada* es la entrada que se va a quitar, y *valor* sea `""` o `dword:00000000`.  
  
 Para excluir varias entradas de una clave del registro, se trata de enumerar la clave una vez seguido por una línea para cada entrada excluir.  
  
 Para excluir una clave de registro completo de una aplicación de shell aislado, agregue la clave en el archivo de aplicación .pkgundef pero no se especifica ninguna entrada del registro para esa clave.  
  
 Puede agregar comentarios al archivo .pkgundef. Una sola línea de comentario debe tener dos barras diagonales como los dos primeros caracteres.  
  
 Por ejemplo, para quitar el **conectar con base de datos** y **conectar al suministro r** comandos en el **herramientas** menú, puede quite el comentario de la línea:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 y agregue la línea:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 archivo .pkgundef de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [GUID del paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizar el Shell aislado](../extensibility/customizing-the-isolated-shell.md)

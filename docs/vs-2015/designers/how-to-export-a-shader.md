---
title: 'Cómo: Exportar un sombreador | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8c3a6ea90b43caeb1140cbb9ab7c699bdb09c3e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213296"
---
# <a name="how-to-export-a-shader"></a>Cómo: Exportar un sombreador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Diseñador de sombras para exportar un sombreador del lenguaje DGSL (Directed Graph Shader Language) para poder usarlo en la aplicación.  
  
 Este documento muestra esta actividad:  
  
-   Exportar un sombreador  
  
## <a name="exporting-a-shader"></a>Exportar un sombreador  
 Después de crear a un sombreador mediante el Diseñador de sombras y antes de poder usarlo en la aplicación, tendrá que exportarlo en un formato compatible con la API de gráficos. Puede exportar un sombreador de maneras diferentes para satisfacer distintas necesidades.  
  
#### <a name="to-export-a-shader"></a>Para exportar un sombreador  
  
1.  En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra un archivo **Gráfico de sombreador visual (.dgsl)**.  
  
     Si no tiene un archivo **Gráfico de sombreador visual (.dgsl)** para abrir, cree uno como se describe en [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  En la barra de herramientas del **Diseñador de sombras**, seleccione **Avanzadas**, **Exportar**, **Exportar como**. Se muestra el cuadro de diálogo **Exportar sombreador**.  
  
3.  En la lista desplegable **Guardar como tipo**, elija el formato que quiere exportar.  
  
     Estos son los formatos que puede elegir:  
  
     **Sombreador de píxeles HLSL (\*.hlsl)**  
     El sombreador se exporta como código fuente del lenguaje HLSL (High Level Shader Language). Esta opción permite modificar el sombreador más tarde, incluso después de que se implemente en una aplicación. Esto puede hacer más fácil de depurar y revisar el código en función de los problemas del usuario final, pero también resulta más fácil para un usuario modificar el sombreador de maneras no deseadas, por ejemplo para obtener una ventaja desleal en un juego competitivo. Es posible que también aumente el tiempo de carga del sombreador.  
  
     **Sombreador de píxeles compilados (\*.cso)**  
     Exporta el sombreador como código de bytes HLSL. Esta opción permite modificar el sombreador más tarde, incluso después de que se implemente en una aplicación. Esto puede hacer más fácil de depurar y revisar el código en función de los problemas del usuario final, pero dado que el sombreador está precompilado, no genera una sobrecarga adicional en tiempo de ejecución cuando se carga en la aplicación. Los usuarios lo suficientemente cualificados todavía pueden modificar el sombreador de maneras no deseadas, pero la compilación del sombreador lo hace mucho más difícil.  
  
     **Encabezado de C++ (\*.h)**  
     Exporta el sombreador como un encabezado de estilo C que define una matriz de bytes que contiene el código de bytes HLSL. Esta opción puede ralentizar la depuración y la revisión del código en función de los problemas del usuario final, dado que es necesario volver a compilar la aplicación para probar la corrección. Pero como esta opción hace que sea difícil, aunque no imposible, modificar el sombreador después de implementarse en una aplicación, presenta la mayor dificultad para un usuario que quiere modificar el sombreador de formas no deseadas.  
  
4.  En el cuadro combinado **Nombre de archivo**, especifique un nombre para el sombreador exportado y, después, pulse el botón **Guardar**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md)   
 [Diseñador de sombras](../designers/shader-designer.md)




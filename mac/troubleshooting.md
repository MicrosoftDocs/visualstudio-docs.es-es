---
title: Solución de problemas
description: Problemas comunes y soluciones para usuarios de Visual Studio para Mac.
ms.topic: troubleshooting
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: b0f10e1f70349126ab48c41efc40f982212836f1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691884"
---
# <a name="troubleshooting"></a>Solución de problemas

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Visualización de registros en Visual Studio para Mac

Para ver los registros, vaya al elemento de menú **Ayuda > Abrir directorio de registro**, como se muestra debajo:

![Elemento de menú Abrir directorio de registro](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Visualización de excepciones

Cuando se detecta una excepción, aparece una burbuja de excepción. Para ver más detalles, seleccione el botón **Ver detalles**:

![Visualización de más detalles sobre una excepción](media/troubleshooting-image2.png)

Este muestra el cuadro de diálogo **Mostrar detalles**, que proporciona más información sobre la excepción:

![Cuadro de diálogo Mostrar detalles](media/troubleshooting-image3.png)

A continuación se describen detalladamente las secciones importantes del cuadro de diálogo que vienen numeradas arriba:

1. El tipo de excepción, que muestra el nombre completo del tipo de excepción que se va a observar.
2. El mensaje de excepción, que muestra el valor de la propiedad Mensaje del objeto de excepción.
3. El tipo de excepción interna, que muestra el nombre completo del tipo de excepción de la excepción seleccionada en la vista de árbol de excepción interna.
4. El mensaje de excepción interna, que muestra el valor de la propiedad Mensaje de la excepción seleccionada en la vista de árbol de excepción interna.
5. Vista Seguimiento de la pila. Se puede contraer mediante una flecha de cierre y contiene entradas de marcos de pila.
6. Ejemplo de entradas de código de no usuario.
7. Ejemplo de entradas de código de usuario.
8. Vista Propiedades, que muestra todas las propiedades y los campos de la excepción. Se puede contraer mediante una flecha de cierre.
9. Vista de árbol de excepción interna. Seleccione las excepciones internas de esta vista con las flechas arriba o abajo del teclado o con el mouse o el panel táctil.
10. De forma predeterminada, está establecido en lo que esté establecida la opción **Solo depurar el código del proyecto** de la configuración del depurador. Al activar esta casilla se permite que todo el código de no usuario se contraiga en una línea en el seguimiento de la pila.
11. Un botón Copiar para copiar la salida `exception.ToString()` en el Portapapeles.

Tenga en cuenta que algunas de estas secciones solo están visibles si la excepción tiene una excepción interna.

## <a name="see-also"></a>Consulte también

- [Resources for troubleshooting IDE errors (Visual Studio on Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors) (Recursos para solucionar errores de IDE [Visual Studio en Windows])
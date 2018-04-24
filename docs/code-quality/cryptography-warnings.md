---
title: Advertencias de criptografía
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b36e174b577ccdb455e88b4bb10f061bfd2396a3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="cryptography-warnings"></a>Advertencias de criptografía
Las advertencias de criptografía admiten bibliotecas y aplicaciones más seguras gracias al uso correcto de criptografía. Estas advertencias ayudan a evitar los errores de seguridad en su programa. Si deshabilita cualquier advertencia de este tipo, se debe indicar el motivo claramente en el código además de informar al responsable de seguridad designado a ese proyecto de desarrollo.

|Regla|Descripción|
|----------|-----------------|
|[CA5350: Do Not Use Weak Cryptographic Algorithms (No use algoritmos criptográficos no seguros)](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Las funciones hash y los algoritmos de cifrado débiles se usan hoy en día para numerosos propósitos, pero no se recomiendan para garantizar la confidencialidad o la integridad de los datos que se protegen.        Esta regla se desencadena cuando se encuentran los algoritmos TripleDES, SHA1 o RIPEMD160 en el código.|
|[CA5351: Do Not Use Broken Cryptographic Algorithms (No use algoritmos criptográficos rotos)](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Los algoritmos criptográficos rotos no se consideran seguros y debe desalentarse su uso. Esta regla se desencadena cuando encuentra el algoritmo hash MD5 o los algoritmos de cifrado DES o RC2 en el código.|
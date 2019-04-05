---
title: Manual de referencia de IntelliTest | Herramientas de pruebas para desarrolladores de Microsoft
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d7258549b242091737e14e00980447eb48d5e78b
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324804"
---
# <a name="intellitest-reference-manual"></a>Manual de referencia de IntelliTest

## <a name="contents"></a>Contenido

* **[Información general de IntelliTest](introduction.md)**
  - [Hello World, de IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Limitaciones](introduction.md#limitations)
    * [Indeterminismo](introduction.md#nondeterminism)
    * [Simultaneidad](introduction.md#concurrency)
    * [Código nativo](introduction.md#native-code)
    * [Plataforma](introduction.md#platform)
    * [Idioma](introduction.md#language)
    * [Razonamiento simbólico](introduction.md#symbolic-reasoning)
    * [Seguimientos de pila incorrecto](introduction.md#incorrect-stack-traces)
  - [Información adicional](introduction.md#further-reading)

* **[Introducción a IntelliTest](getting-started.md)**
  - [Atributos importantes](getting-started.md#important-attributes)
  - [clases del asistente estáticas importantes](getting-started.md#helper-classes)

* **[Generación de pruebas](test-generation.md)**
  - [Generadores de pruebas](test-generation.md#test-generators)
  - [Pruebas unitarias con parámetros](test-generation.md#parameterized-unit-testing)
  - [Pruebas unitarias genéricas con parámetros](test-generation.md#generic-parameterized)
  - [Permisos para excepciones](test-generation.md#allowing-exceptions)
  - [Pruebas de tipos internos](test-generation.md#internal-types)
  - [Hipótesis y aserciones](test-generation.md#assumptions-and-assertions)
  - [Condición previa](test-generation.md#precondition)
  - [Condición posterior](test-generation.md#postcondition)
  - [Errores de pruebas](test-generation.md#test-failures)
  - [Configuración y desmontado](test-generation.md#setup-teardown)
  - [Información adicional](test-generation.md#further-reading)

* **[Generación de entradas](input-generation.md)**
  - [Solucionador de restricciones](input-generation.md#constraint-solver)
  - [Cobertura de código dinámico](input-generation.md#dynamic-code-coverage)
  - [Números enteros y flotantes](input-generation.md#integers-and-floats)
  - [Objects](input-generation.md#objects)
  - [Creación de instancias de las clases existentes](input-generation.md#existing-classes)
  - [Visibilidad](input-generation.md#visibility)
  - [Bocetos con parámetros](input-generation.md#parameterized-mocks)
  - [Structs](input-generation.md#structs)
  - [Matrices y cadenas](input-generation.md#arrays-and-strings)
  - [Obtención de entradas adicionales](input-generation.md#additional-inputs)
  - [Información adicional](input-generation.md#further-reading)

* **[Límites de exploración](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Glosario de atributos](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Cascada de configuración](settings-waterfall.md)**

* **[clases del asistente estáticas](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Advertencias y errores](warnings-and-errors.md)**
  - [MaxBranches superado](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime superado](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions superado](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls superado](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack superado](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns superado](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests superado](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [No se puede concretizar la solución](warnings-and-errors.md#cannot-concretize-solution)
  - [Se necesita ayuda para construir el objeto](warnings-and-errors.md#help-construct)
  - [Se necesita ayuda para buscar tipos](warnings-and-errors.md#help-types)
  - [Tipo utilizable estimado](warnings-and-errors.md#usable-type-guessed)
  - [Error inesperado durante la exploración](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Método no instrumentado llamado](warnings-and-errors.md#uninstrumented-method-called)
  - [Método externo llamado](warnings-and-errors.md#external-method-called)
  - [Método sin capacidad de instrumentación llamado](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problema de capacidad de prueba](warnings-and-errors.md#testability-issue)
  - [Limitación](warnings-and-errors.md#limitation)
  - [Error de coincidencia de llamadas observado](warnings-and-errors.md#observed-call-mismatch)
  - [Se almacenó un valor en el campo estático](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>¿Tiene comentarios?

Publique sus ideas y solicitudes de características en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
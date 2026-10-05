# The objects, rules and layers inside one module

**30. Keep business rules in one domain layer, apart from screens and storage.** (LAYERED ARCHITECTURE, chapter 4:
*strengthens*.) That is the part of the code an agent can load whole and change without loading the rest. Point the
agents there for rule changes, and check the layer rules with a tool.

**31. Track by identity only what must be tracked; make the rest values.** (ENTITIES, chapter 5: *holds*; VALUE
OBJECTS, chapter 5: *holds*.) Agents do not change which things have an identity of their own.

**32. Give each root that is looked up a repository, and keep storage out of the model.** (REPOSITORIES, chapter
6: *holds*.)

**33. Put the knowledge of how to assemble a complex object in exactly one place, and write down where.** (FACTORIES,
chapter 6: *holds*; Site the FACTORY where control belongs, chapter 6: *bends*.) Agents copy the nearest example,
not the designer's reasoning.

**34. Keep logic in functions without side effects, and push the rest to the edges.** (SIDE-EFFECT-FREE FUNCTIONS,
chapter 10: *holds*.) They stay predictable for whoever calls them, person or agent.

**35. Keep each concept's dependencies to the ones it needs.** (STANDALONE CLASSES, chapter 10: *strengthens*.) Every
dependency is context an agent must load.

**36. Make the design supple before you scale the agents on it.** (Supple design, chapter 10: *strengthens*.)
Agents change code fast; only a design that names its concepts and states its rules lets them change it without
breaking something else.

**37. When the business has several ways to do a thing, make each a named policy.** (STRATEGY, chapter 12: *holds*.)
A new discount or a new claim type is then a new policy, not a new branch in every caller.

**38. Cut the code where the business itself divides.** (CONCEPTUAL CONTOURS, chapter 10: *holds*.) Agents make the
cuts cheaper, not wiser.

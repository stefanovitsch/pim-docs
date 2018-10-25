Configure Entity Limits
=======================

For the Reference Entities feature (*introduced in 3.0*), some limits about number of entities have been defined to guarantee that the PIM is functional and runs smoothly.
However, as your catalog is very unique, **you may need to raise those values**, this chapter explains how.

All those limits are defined as parameters that you can override like any other `Symfony config parameter <https://symfony.com/doc/3.4/best_practices/configuration.html>`_.

Raise the limit of Reference Entities you can create
----------------------------------------------------
By default, you can't create more than **100** Reference Entities.
If you want to create more, you have to edit the ``reference_entity_limit`` parameter:

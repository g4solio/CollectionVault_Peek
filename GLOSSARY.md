# Glossary

The domain terms of the project. Each term is the English word used in code, docs, issues and the English interface, followed by the word the primary interface language shows. Each _Avoid_ list gives the words not to use, so that one thing never has two names.

## Rules

- **One name per thing.** A stored value is its English label in snake_case. A code name uses the same words as its stored key: PascalCase in C#, snake_case in the document. No serialization overrides.
- **Code names use the whole term** and none of its _Avoid_ words. A test checks the parts a script can.
- **The core writes no text meant for people.** It records a kind and its data; the interface words it from the label files. Exception messages are for developers.
- **Interface labels live in `labels/<lang>.json`**, one flat object keyed by the core's own names. One test proves every language file complete against the core and this glossary.
- **Old stored documents keep their old words.** A rename of a stored key lands only with the schema step that converts older documents, and the fixtures that hold old documents are never translated.
- **A term the glossary lacks is a signal.** Either the language is being invented (reconsider) or the glossary has a gap (fill it in the same pull request).

## Example entries

The domain below is a stand-in. Replace it with yours and keep the shape.

**Order** (it: Ordine):
A customer's request to buy, from the moment it is placed until it is fulfilled or cancelled. One Order has one or more Line items.
_Avoid_: purchase, cart (a cart is not yet an Order), transaction (it: acquisto, carrello)

**Line item** (it: Riga):
One product at one quantity inside an Order. Two of the same product at different prices are two Line items.
_Avoid_: item, product line, entry (it: articolo, voce)

**Fulfilment** (it: Evasione):
The act of handing an Order's goods to the carrier. An Order has at most one Fulfilment; a partial shipment is a Fulfilment of some Line items with the rest still open.
_Avoid_: shipping (the carrier's part), delivery (the customer's part) (it: spedizione, consegna)

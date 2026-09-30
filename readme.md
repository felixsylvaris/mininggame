# About

This is a tiny vibecoded HTML/JS game.

You run a small space-mining company. You manage crew, equipment, mining operations, inventory, customers, suppliers, and cash.

The core game is a spreadsheet-style business simulator, with a Tetris-like mining/processing minigame as the operational layer.

The game is designed around real business principles rather than space-combat mechanics. It could potentially work as a simple educational game for high-school economics classes.

Space terminology is used for flavor. For example, instead of paying ordinary taxes, the company might pay a Space Company License.

# Core gameplay loop

Assign workers → choose asteroid → mine → manage inventory → buy supplies → sell products → pay expenses → invest → repeat.

## Time

One turn = one month.
12 turns = one year.

## Initial objective

Keep the company solvent and grow its cash flow.

## Long-term objective

Build a larger and more profitable space-mining business through better equipment, workers, financing, processing, contracts, and vertical integration.

Initial workers

Four workers, each with a name, wage, and assigned role:

Miner Pilot — required for mining.
Mechanic — reduces the risk/consequences of vessel breakdowns.
Staffer — handles general base work such as cooking and cleaning.

Wages are paid every turn. Minimum wage is 5 credits, but the player can set higher wages.

### Initial expenses

Wages
Food
Maintenance

Initial revenue

Sale of mined ore

### Mining

The player chooses from 10 asteroids. Each asteroid has:

Resource type
Remaining deposit
Extraction difficulty/ease

Initial resources:

Water — cheap, high demand, high mass
Silica
Carbon — high demand, high mass
Heavy minerals
Rare minerals — rare, expensive, shallow deposits

The company initially owns one drill vessel.

Each month, the vessel extracts:

ceil(10 × extraction ease)

The selected asteroid remains selected for the following turn unless the player changes it.

## Trading

The company can conduct regular monthly trades.

The player sells mined products and buys supplies such as food and spare parts.

Buy orders require available cash, so selling inventory before buying supplies can become important.

Emergency trades are also available, presumably at worse prices.

 Testing cheat

A temporary Get Space Union Funds button adds 10,000 credits. This exists purely to prevent repeated bankruptcy while testing the game.

## Future systems

Hiring, wages and worker training
Equipment maintenance and upgrades
Base operations
Administration / HR
Security
Taxes/licensing
Loans and other financing
Customers and suppliers
Product selection and market strategy
Processing/refining
Vertical integration
R&D
Licensing
Marketing and contract acquisition

### Not yet implemented

Tetris mining/processing minigame
Romance with Space Margaret Thatcher
API comparison with AI frontier companies

# Kessler & Vance Extraction Co.

A tiny vibecoded HTML/JS game. You run a small independent asteroid-mining company: crew, vessels, rooms, mining, inventory, contracts, loans and cash.

It is a spreadsheet-style business simulator built around real business principles rather than space combat. Space terminology is flavor only (for example, a future tax could be a "Space Company License"). It is designed as an educational economics game for high-school classes, so the **balance sheet is a first-class feature**: every action is booked properly.

Everything lives in one file (`Kessler & Vance Extraction Co.html`). There is no backend and no save/load yet, so a page refresh restarts the game.

---

## Core loop

Assign workers -> choose asteroid -> advance the month -> mine -> manage inventory -> buy supplies -> sell products -> pay expenses -> invest -> repeat.

**Time:** one turn = one month, 12 turns = one year.

**Initial objective:** stay solvent and grow cash flow.
**Long-term objective:** build a larger, more profitable business through better equipment, workers, financing, contracts, processing and vertical integration.

---

## Starting position

| Item | Start |
|---|---|
| Cash | 600 cr |
| Food / Spare parts | 20 / 12 (booked at 1.5 cr / 3 cr) |
| Crew | Rook Adisa (Pilot, 12 cr), Denny Okafor (Mechanic, 10 cr), Mira Solheim and Tobin Kaur (Staffers, 5 cr) |
| Vessel | 1x TrashCrash |
| Rooms | CEO Office, Habitat 5, Hangar, Warehouse 100 (5 Opp needed vs 8 produced by Staffers) |
| Asteroids | 10 known: 1 mapped Water ice at exact base stats, 9 random and unmapped |
| Owner capital | 5,466 cr (cash, supplies, vessel and starting rooms all contributed by the owners) |

---

## What is in the game (tabs)

### Operations
- **Fleet & mining:** one card per vessel with condition bar, rust, efficiency on the selected asteroid, and Pilot / Asteroid dropdowns.
- **Known asteroids (max 20):** resource, remaining deposit, ease, status. `X` removes an asteroid from the list, `M` maps it for 100 cr (required before extraction). **Scout** (50 cr) adds one random asteroid, unmapped.
- **Sell cargo / Buy supplies:** sell any amount of ore at the current spot price; buy food and spare parts at standard cost.
- **Emergency trades:** sell the whole cargo hold at 70% of price, or buy 10 food at 2x price.
- **Operations log:** the last 10 events.
- **Quick Loan:** +100 cr now, repay 34 cr/month for 3 months, up to 5 at once.
- **Get Space Union Funds:** testing cheat, +10,000 cr booked as an equity grant.
- **Advance to next month:** runs the whole monthly cycle (see below).

### HR
- **Crew table:** name and skill badges, role, wage (with the worker's expected wage shown), tenure and efficiency, `X` to fire.
- **Hiring:** Staffer (min 5 cr), Mechanic (min 10 cr), Pilot (min 12 cr). Recruitment fee 10 cr each. Hiring is blocked when the habitat is full.
- **Training panel** and **Operations panel** (see Systems).

### Equipment
- **Your vessels:** book value and sale price, with a **Sell** button.
- **Buy a vessel:** catalog with per-resource efficiency, or **borrow** a RainbowDust at 200 cr/month for a number of months you choose.
- **Rooms:** owned rooms, a build menu, and a summary of hangar slots, bunks, storage and Opp.

### Balance sheet
- Assets on the left, liabilities and equity on the right, in the layout of a classroom balance sheet.
- Monthly revenue / expenses / net for the current year. When month 12 closes, the year collapses into a **Past years** table with revenue, expenses, net, closing cash and assets at month 12.

### Loans & bonds
- **Bonds we issue** (borrowing) and **Trade Union bonds** (our investment).

### Contracts
- Long-term monthly **buy** and **sell** contracts.

---

## Systems in detail

### Monthly cycle (order of events)
1. Tenure +1 month for everyone (+2 for trainees). Every 24 months of tenure, +1 cr raise. Retirements and January resignations. Training progress.
2. Pay wages.
3. Crew eats. Each worker eats 1 food, plus 1 more if there is no Staffer. If food runs short, mining output is halved that month.
4. Bond interest and repayments, Quick Loan instalments, Trade Union bond accrual and maturity.
5. For each vessel: age +1 month, condition -8, repairs, breakdown roll, depreciation or lease rent, then mining.
6. Contracts execute.
7. Ore prices drift randomly by -10% to +10%.
8. Month books close into retained earnings.

### Mining
- Each pilot-assigned vessel on a mapped asteroid mines: `ceil(10 x ease x (1 + pilot efficiency))`, multiplied by the vessel's efficiency for that ore, by condition%, by 0.5 if the crew is hungry, and by `(1 - rust%)`. The result is capped by the remaining deposit.
- No pilot, no asteroid, a depleted asteroid or a breakdown means the vessel stays docked.
- Asteroid stats: base deposit / ease is Water 200 / 2.0, Carbon 100 / 1.5, Silica 80 / 1.0, Iron (heavy) 60 / 0.6, Rare 30 / 0.3. Each value varies from 50% to 200% (so Water can be 100 / 1.0 or 400 / 4.0). Names are a Greek letter plus a Latin word, like "Sigma Garum".
- **Storage:** mining happens first and only what fits in warehouse space is stored. The rest is lost, though the deposit still depletes. Ore counts against storage; food and parts do not.

### Vessels

| Vessel | Price | Water | Silica | Carbon | Iron | Rare |
|---|---|---|---|---|---|---|
| TrashCrash | 3,000 | 0.75 | 0.75 | 0.75 | 0.75 | 0.75 |
| RainbowDust | 6,000 | 1.0 | 1.0 | 1.0 | 1.0 | 1.0 |
| BaskShark | 5,000 | 2.0 | 0.75 | 1.0 | 0.5 | 0.6 |
| BlackMamba | 8,000 | 1.0 | 0.9 | 1.5 | 0.6 | 0.8 |
| DiamonHands | 10,000 | 0.8 | 0.9 | 1.0 | 1.4 | 0.9 |
| SiSenior | 9,000 | 0.8 | 1.5 | 0.9 | 1.0 | 1.1 |
| GoldDigger | 15,000 | 0.7 | 1.2 | 0.9 | 1.0 | 1.4 |

- Bought vessels depreciate straight-line over 60 months. They sell for 50% of the new price at any age; the difference from book value is booked as a gain or loss.
- **Condition and repair:** condition drops 8 per month. Each month, parts repair it (10 points per part). Below 40 condition, a vessel has a 30% monthly breakdown chance, or 10% if you employ a Mechanic.
- **Rust:** each 12 months of age adds 1% rust. Rust % is the chance a mining vessel eats one extra spare part that month, and it also lowers the vessel's efficiency by the same %.

### Workers
- **Efficiency** = tenure bonus + overpay bonus - understaffing penalty.
  - Tenure: months employed / 3, capped at +25%. Tenure keeps accumulating beyond the cap.
  - Overpay: +1% per 5% paid above the expected wage, capped at +20% (reached at double pay).
  - Pilots: efficiency multiplies asteroid ease. Mechanics: efficiency is the chance a repair uses no parts. Staffers: efficiency scales Operations output.
- **Raises:** company policy gives every worker +1 cr every 24 months.
- **Resignation:** each January, workers paid less than 30% above their expected wage have a 1% chance to resign.
- **Retirement:** at 300 months a worker retires and buys a cinnamon farm on Terra.
- **Expected wage:** set when hired (role minimum) and raised by training. Wages can't be set below it.
- **Skills:** each worker carries Pilot / Mechanic flags. A role can only be assigned if the worker has that skill.

### Training
- Only **Idle** workers can train. Pick **Train Pilot** or **Train Mech**; they become "Training" for 6 months and do no work, but are still paid.
- They keep their tenure and gain it at double speed during training.
- At graduation they gain the skill flag and return to Idle. Their expected wage rises **once, at graduation**: +3 cr for Pilot, +2 cr for Mechanic (stacking if both). Their pay is lifted to the new expected wage if below it.
- This makes training a cheaper route to specialists: a 5 cr Staffer becomes an 8 cr Pilot, instead of hiring one at 12 cr.

### Rooms and Operations (Opp)

| Room | Cost | Opp | Provides |
|---|---|---|---|
| CEO Office | 200 | 1 | Only one needed |
| Habitat 5 | 500 | 1 | 5 worker bunks |
| Hangar | 1,000 | 2 | 1 vessel slot (owned or leased) |
| Warehouse 100 | 100 | 1 | 100 ore units |
| Warehouse 500 | 800 | 2 | 500 ore units |
| Warehouse 1000 | 2,000 | 3 | 1,000 ore units |

- Rooms **need** Opp (the table); Staffers **produce** it, 4 each, scaled by efficiency.
- Every whole missing Opp gives **-5% efficiency to all workers**. A red banner appears when understaffed.
- Hiring is blocked without a free bunk; buying or borrowing a vessel is blocked without a free hangar slot (sell a vessel to make room).
- Rooms are fixed assets at cost, with no depreciation, and count at 75% toward bond collateral.

### Contracts
Monthly orders with a quantity and length you choose within these limits.

| Buy contracts | Qty/mo | Months | Price |
|---|---|---|---|
| Food | 1-20 | 3-24 | 1 cr |
| Spare parts | 1-20 | 3-24 | 2 cr |

| Sell contracts | Qty/mo | Months | Price |
|---|---|---|---|
| Water ice | 5-60 | 6-24 | 3 cr |
| Carbon | 3-50 | 6-24 | 6 cr |
| Silica | 3-30 | 6-24 | 12 cr |
| Heavy minerals (iron) | 2-20 | 6-24 | 20 cr |
| Rare minerals | 1-10 | 6-24 | 60 cr |

If a sell contract can't be filled from stock, the shortfall is bought from the spot market at that month's price, and you still get the contract price.

### Financing
- **Collateral value** = 100% cash + 75% fixed assets (vessels and rooms, net) + 50% food and parts + 25% ore. **Bond capacity** = collateral / 100, rounded up.
- **Bonds we issue** (100 cr each, interest of rate/12 monthly, principal repaid at the end): 12 months at 6%, 24 months at 7%, 48 months at 10%. Buy several at once; outstanding bonds are listed with months left.
- **Trade Union bonds** (we invest): 100 cr each, 3-12 months, 1.5%. Value grows by rate/12 per month and pays out at term. Cashing out early costs 1 cr per bond. Deliberately a poor investment.
- **Quick Loans:** 100 cr now, 34 cr/month for 3 months (a 2 cr cost booked at once), up to 5 outstanding, shown as a liability.

### Accounting rules (for teachers)
- Revenue: ore sales, contract income, Trade Union bond accrual, gains on vessel sales and purchases below standard cost.
- Expenses: wages, food eaten, parts used, interest, vessel depreciation, lease rent, mapping, scouting, hiring fees, early cash-out penalties, losses on vessel sales and purchases above standard cost.
- Buying a vessel or room is an asset swap (cash for fixed assets), not an expense.
- Ore inventory is valued at market price on the balance sheet. An **inventory valuation reserve** in equity offsets it so the sheet balances.
- Food and parts are held at standard cost; the gap to the price paid goes to revenue or expense.

---

## Update history

Features were designed in this order (grouped by the original "Next Update" notes).

1. **Core game:** monthly loop, one TrashCrash, 4 workers, 10 asteroids, selling ore, buying food and parts, emergency trades, test cheat.
2. **Hiring, vessels, balance sheet:** hire by role with recruitment fee and minimum wages; buy several vessels with 60-month depreciation; TrashCrash and RainbowDust, plus leasing; proper balance sheet with year roll-ups.
3. **Loans, selling vessels, contracts:** Loans & Bonds tab with collateral limit; sell vessels at 50% of new price; Contracts tab.
4. **Know-how and new boat:** worker tenure efficiency (pilot ease multiplier, mechanic free repairs), BaskShark.
5. **Trade Union bonds** as a poor-return investment.
6. **Asteroid management, Equipment tab, new ships:** 20-asteroid cap, X / M icons, Scout, Greek + Latin names, 50%-200% stat variance; Equipment tab for vessel buying and selling; BlackMamba, DiamonHands, SiSenior, GoldDigger.
7. **Quick Loans, past-year assets, rust, HR tab:** Quick Loan button and liability; assets at month 12 in past years; vessel age and rust; HR tab with firing, 24-month raises, January resignations, 300-month retirement, overpay efficiency.
8. **Training and Operations:** Pilot/Mechanic skill flags, 6-month training of Idle workers, wage bump at graduation (+3 / +2), Staffers produce 4 Opp.
9. **Rooms:** CEO Office, Habitat, Hangar and Warehouses with Opp requirements, bunk / hangar / storage limits and the understaffing penalty.

---

## Not yet implemented / ideas

- Tetris-like mining / processing minigame
- Taxes and licensing (Space Company License)
- Security, administration and HR overhead
- Customers and suppliers, product selection and market strategy
- Processing / refining, vertical integration
- R&D, marketing and contract acquisition
- Selling or demolishing rooms, room depreciation
- Save / load
- Romance with Space Margaret Thatcher
- API comparison with AI frontier companies

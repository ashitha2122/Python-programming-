BASE_RATE = Decimal("32.00")
STANDARD_FAT = Decimal("3.5")
FAT_STEP_RATE = Decimal("0.45")
BONUS_LIMIT = Decimal("500")
BONUS_RATE = Decimal("0.50")
STANDARD_SNF = Decimal("8.5")
SNF_STEP_RATE = Decimal("0.00")
MIN_FAT = Decimal("3.5")
MAX_FAT = Decimal("6.0")
MIN_SNF = Decimal("8.5")
MAX_SNF = Decimal("10.0")
def calculate_payment(fat, snf, litres, month):
 if month not in range(4, 7):
 raise ValueError("Seasonal rate applies from April to June")
 if not MIN_FAT <= fat <= MAX_FAT:
 raise ValueError("Fat percentage is outside the allowed range")
 if not MIN_SNF <= snf <= MAX_SNF:
 raise ValueError("SNF percentage is outside the allowed range")
 if litres < 0:
 raise ValueError("Litres cannot be negative")
 rate = BASE_RATE
 rate += (fat - STANDARD_FAT) * FAT_STEP_RATE
 rate += (snf - STANDARD_SNF) * SNF_STEP_RATE
 if litres > BONUS_LIMIT:
 rate += BONUS_RATE
 rate = rate.quantize(
 Decimal("0.01"),rounding=ROUND_HALF_UP
 )
 total = (rate * litres).quantize(
 Decimal("0.01"),
 rounding=ROUND_HALF_UP
 )
 return rate, total
try:
 fat = Decimal(input("Enter fat percentage: "))
 snf = Decimal(input("Enter SNF percentage: "))
 litres = Decimal(input("Enter total litres for 10 days: "))
 month = int(input("Enter month number (4 for April, 5 for May, 6 for June): "))
 rate, total = calculate_payment(fat, snf, litres, month)
 print(f"Payment rate: Rs.{rate:.2f} per litre")
 print(f"Total payment: Rs.{total:.2f}")
except (ValueError, ArithmeticError) as error:
 print("Error:", error)

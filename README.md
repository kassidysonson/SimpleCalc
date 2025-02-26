package com.example.creditcards

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.util.TypedValue
import android.view.View
import android.widget.Button
import android.widget.ImageView
import android.widget.Spinner
import android.widget.TextView


class MainActivity : AppCompatActivity() {


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)


        val findCard = findViewById<Button>(R.id.find_card)
        findCard.setOnClickListener {
            val creditCard = findViewById<Spinner>(R.id.credit_card)
            val choice = creditCard.selectedItem
            val creditList = getCreditCard(choice.toString())
            val credit = creditList.reduce { str, item -> str + '\n' + item }
            val brands = findViewById<TextView>(R.id.brands)
            brands.text = credit
            val chooseCard = findViewById<Button>(R.id.choose_card)
            val displayInfo=findViewById<TextView>(R.id.display_info)
            val requestInfo=findViewById<TextView>(R.id.request_info)
            val submit=findViewById<Button>(R.id.submit)
            val card_picture=findViewById<ImageView>(R.id.gen_card)
            chooseCard.visibility=View.VISIBLE






            // choose card button - congrats!
            chooseCard.setOnClickListener {
                val selectedCard = creditCard.selectedItem.toString()
                val message =
                    "Congratulations, you are now a cardholder at $selectedCard !\n\nPlease give $selectedCard 7-14 business days for your card to be sent to your requested address. Please enter address below:  "
                brands.text = message

                //prompt name
                requestInfo.visibility=View.VISIBLE
                displayInfo.visibility=View.VISIBLE
                submit.visibility=View.VISIBLE
                card_picture.visibility=View.GONE





            }

            submit.setOnClickListener {
                val address=displayInfo.text.toString()
                requestInfo.visibility=View.GONE
                displayInfo.visibility=View.GONE
                submit.visibility=View.GONE
                chooseCard.visibility=View.GONE
                card_picture.visibility=View.VISIBLE
                card_picture.setImageResource(R.drawable.cardpic)
                val finale ="Your card is on the way to $address! Please take a moment to review the Terms and Conditions, which detail your rights and responsibilities as a cardholder."
                brands.text=finale





            }

            //text size
            brands.setTextSize(TypedValue.COMPLEX_UNIT_SP, 17f)
            brands.setTypeface(null, android.graphics.Typeface.BOLD)
            //color of string text
            brands.setTextColor(resources.getColor(R.color.colorText, theme))
        }
    }

        fun getCreditCard(color: String): List<String> {
            return when (color) {
                "Discover" -> listOf(
                    "Best Fit: Discover it Student Cash Back\n",
                    "Category: Best for university students with limited or nonexistent credit history\n",
                    "Intro APR: ",
                    "0% intro APR on purchases for 6 months\n",
                    "Variable APR:",
                    "18.24% to 27.24% variable\n",
                    "Annual Fee: $0\n",
                    "Rewards: ",
                    "Earn 5% cash back on each quarter’s activated rotating categories on up to $1,500 in combined purchases, then 1% (no expiration)\n",
                    "Bonus Offer(s): \n",
                    "25,000 online bonus points if you make at least $1,000 in purchases in the first 90 days of your account opening "
                )

                "Bank of America" -> listOf(
                    "Best Fit: Bank of America Travel Rewards for Students\n",
                    "Category: Best for university students with an average credit history\n",
                    "Intro APR: ",
                    "0% Intro APR for your first 15 billing cycles for purchases, and for any balance transfers made within the first 60 days of opening your account\n",
                    "Variable APR:",
                    "18.74% to 29.99% variable\n",
                    "Annual Fee: $0\n",
                    "Rewards: ",
                    "Earn unlimited 1.5 points for every $1 you spend on all purchases everywhere, every time and no expiration on points as long as your account remains open (no expiration)\n",
                    "Bonus Offer(s): \n",
                    "25,000 online bonus points if you make at least $1,000 in purchases in the first 90 days of your account opening "
                )

                "Capital One" -> listOf(
                    "Best Fit: Capital One QuickSilver Student Cash Rewards\n",
                    "Category: Best for university students new to credit\n",
                    "Intro APR: ",
                    "N/A\n",
                    "Variable APR:",
                    "19.99% to 29.99% variable\n",
                    "Annual Fee: $0\n",
                    "Rewards: ",
                    "Earn unlimited 1.5% cash back on every purchase, every day (no expiration)\n",
                    "Bonus Offer(s): \n",
                    "Earn a one-time $50 cash bonus once you spend $100 on purchases within 3 months from account opening"
                )

                else -> listOf(
                    "Best Fit: Navy Federal Credit Union nRewards Secured\n",
                    "Category: Best for individuals who would like upgrade to cashRewards credit card with better benefit, $200 deposit needed\n",
                    "Intro APR: ",
                    "0% intro APR on purchases for 6 months\n",
                    "Variable APR:",
                    "18.00% variable\n",
                    "Annual Fee: $0\n",
                    "Rewards: ",
                    "Earn 1 point for every $1 of net purchases (expires in 4 years of month in which they were earned)\n",
                    "Bonus Offer: ",
                    "Eligible for upgrade to cashRewards credit card"
                )

            }
        }
    }

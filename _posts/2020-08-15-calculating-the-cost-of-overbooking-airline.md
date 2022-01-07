---
layout: post
title: Calculating The Cost Of Overbooking Airline Tickets Using Analytics
date: 2020-08-15 12:13:59.000000000 -04:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Aviation Analytics
tags:
- analytics
- aviation
- business
- data
meta:
  tumblr_carlosaordonez-blog_permalink: https://carlosaordonez-blog.tumblr.com/post/626517493069103104/calculating-the-cost-of-overbooking-airline
  tumblr_carlosaordonez-blog_id: '626517493069103104'
  _oembed_b678fb6edeb3ad7752bcd8ddeefdfeb0: "{{unknown}}"
  _aioseop_title: Analytics behind the cost of overbooking airline tickets
  _aioseop_description: Using Python to calculate max number of overbooking and max
    profit in selling airline tickets.
  amazon_polly_audio_location: ''
  _edit_last: '1'
  _aioseop_keywords: ''
  _aioseop_custom_link: ''
  _aioseop_sitemap_exclude: ''
  _aioseop_disable: ''
  _aioseop_disable_analytics: ''
  _aioseop_noindex: ''
  _aioseop_nofollow: ''
  _aioseop_opengraph_settings: a:14:{s:32:"aioseop_opengraph_settings_title";s:0:"";s:31:"aioseop_opengraph_settings_desc";s:0:"";s:36:"aioseop_opengraph_settings_customimg";s:0:"";s:37:"aioseop_opengraph_settings_imagewidth";s:0:"";s:38:"aioseop_opengraph_settings_imageheight";s:0:"";s:32:"aioseop_opengraph_settings_video";s:0:"";s:37:"aioseop_opengraph_settings_videowidth";s:0:"";s:38:"aioseop_opengraph_settings_videoheight";s:0:"";s:35:"aioseop_opengraph_settings_category";s:8:"activity";s:34:"aioseop_opengraph_settings_section";s:0:"";s:30:"aioseop_opengraph_settings_tag";s:0:"";s:34:"aioseop_opengraph_settings_setcard";s:7:"summary";s:44:"aioseop_opengraph_settings_customimg_twitter";s:0:"";s:44:"aioseop_opengraph_settings_customimg_checker";s:1:"0";}
  amazon_polly_enable: '0'
  _thumbnail_id: '158'
  _yoast_wpseo_content_score: '30'
author:
  login:carordo
  email:
  display_name:
  first_name: Carlos
  last_name: Ordonez
permalink: "/2020/08/15/calculating-the-cost-of-overbooking-airline/"
excerpt: Using Python to calculate max number of overbooking and max profit in selling
  airline tickets.
---
> This article was originally posted on [Linkedin here](https://www.linkedin.com/pulse/calculating-cost-overbooking-airline-tickets-using-carlos/) prior to the pandemic Using Python to calculate the cost of overbooking an airline ticket.
>
> The code can be found in [GitHub here](https://github.com/carordo/Overbooking).

I have been curious to use data analytics in aviation operations. I found that one of the models that airlines use is the binomial function to determine what is the optimum revenue the airline, after calculating the probability of the number of passengers that will show up when overbooking a specific route. The probability is modeled with binomial function assuming that each show or no show sample is independent of each other. This probability is affected by many possible factors like delayed flights, traffic jams, canceling a flight due to personal reasons, etc.

<!-- wp:image {"align":"center","id":116,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/Binomial-function.png" alt="Binomial function" class="wp-image-116"><br>
<figcaption>Binomial function</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph {"align":"justify"} -->

This article was inspired by&nbsp;[Cory Simon](https://github.com/CorySimon)&nbsp;'s article on "[&nbsp;](http://by%20how%20many%20flights%20should%20an%20airline%20overbook/?)[By How Many Flights an Airline Should Overbook](http://corysimon.github.io/articles/by-how-many-flights-should-an-airline-overbook/)". In his analysis, he uses a normal approximation of a binomial distribution. He allocates fixed parameters such as a number of seats per aircraft, the probability of a passenger and expands to a range of additional tickets beyond capacity sold the price per ticket and the price of the voucher. The voucher in his example is defined as the cost the airline incurs to pay passengers for an overbooked ticket.

<!-- /wp:paragraph -->

<!-- wp:paragraph {"align":"justify"} -->

I decided to expand a little more and create a function that could allow passing the value of the ticket, the voucher cost, the number of seats, the probability rate of a passenger showing up and the number of additional seats. I used Python's&nbsp;[numpy cumulative distributive function](https://docs.scipy.org/doc/scipy-0.16.0/reference/generated/scipy.stats.binom.html)&nbsp;to calculate the probability of passengers to show to a flight beyond capacity&nbsp;**(Total Seats Available in the aircraft + total additional overbooking tickets)**. The function also calculates the max number of possible seats available that could be overbooked. This is defined by&nbsp;_p \* x=Total Seats Available_. If the probability is equal to 1 then all seats will be taken. By solving&nbsp;_x_, then&nbsp;_x=Total Seats Available/p&nbsp;_will give the maximum seats available for that probability&nbsp;_p_. A good explanation of the calculation of the probability of overbooking can also be found&nbsp;[here](https://math.stackexchange.com/questions/2426604/binomial-probability-of-airline-overbooking).

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

Let's assume the case of&nbsp; **Embraer 175** &nbsp;flying&nbsp; **Miami to Cleveland with 128 seats** &nbsp;in the main cabin.

<!-- /wp:paragraph -->

<!-- wp:image {"align":"center","id":118,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/Embraer_175.png" alt="Embraer-175-cabin-Layout" class="wp-image-118"><br>
<figcaption>Embraer-175-cabin-Layout</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph {"align":"justify"} -->

For this calculation, I am focused on the number of additional tickets beyond capacity. The following example tests a ticket with a value of $512.00 from Miami to Cleveland in American Airlines, assuming a probability rate of passengers to show at this time on this date at 90%. The maximum number of additional seats the airline could sell is equal to_&nbsp;Max\_Seats = 128 /.9 = 142.22 - 128 = 14.22&nbsp;_rounded down will give&nbsp; **14** &nbsp;additional seats on&nbsp; **128&nbsp;** seat aircraft, with a probability of&nbsp; **90** % of the passengers showing up and a voucher cost for overbooking of&nbsp; **$200.00**.

<!-- /wp:paragraph -->

<!-- wp:image {"align":"center","id":123,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/Air-Fare-example-for-Binomial-Function-750x191.png" alt="Air Fare example for Binomial Function" class="wp-image-123"><br>
<figcaption>Air Fare example for Binomial Function</figcaption>
</figure>

<!-- /wp:image -->

The airline by selling additional tickets increases its revenue, but the net profit decreases if they end up paying for too many vouchers. The voucher cost could include the cost of re-scheduling passengers. In this example, it is omitted. I am trying to find the optimum amount of additional tickets the airline could sell.

<!-- wp:image {"align":"center","id":120,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/overbooking_calculation.jpg" alt="Overbooking Calculation image" class="wp-image-120"><br>
<figcaption>Overbooking Calculation image</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

The result of this graph shows the maximum profit per additional ticket at a fixed voucher cost, with the maximum amount of overbooking tickets (14). The maximum total profit can be reached at $66,995.94 overbooking 6 tickets of the 14.

<!-- /wp:paragraph -->

<!-- wp:image {"align":"center","id":124,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/Expected-Reveneu-vs-tickets-beyond-capacity-graph.jpg" alt="Expected Reveneu vs tickets beyond capacity graph" class="wp-image-124"><br>
<figcaption>Expected Reveneu vs tickets beyond capacity graph</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:image {"align":"center","id":121,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/table_with_overbooking_tickets_sold.jpg" alt="Table with Expected profit by exceeding overbooking" class="wp-image-121"><br>
<figcaption>Table with Expected profit by exceeding overbooking</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

The following table test different vouchers values based on the suggested overbooking tickets found on the previous table.

<!-- /wp:paragraph -->

<!-- wp:image {"align":"center","id":122,"sizeSlug":"large"} -->

<figure class="aligncenter size-large"><img src="/assets/images/2020/08/table_with_overbooking_tickets_max_profit.jpg" alt="Table with Overbooking tickets sold and max profit" class="wp-image-122"><br>
<figcaption>Table with Overbooking tickets sold and max profit</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

The table shows that the ideal&nbsp; **Voucher\_Cost** &nbsp;should be less than $200.00, overbooking 6 seats. If the voucher cost offered is higher than $600.00 the airline should not overbook any additional tickets.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

This analysis is just the first to understand a model, in this case, the binomial function, when applying analytics in aviation operations. It is important to highlight that there are 4 moving variables: Ticket sale price, the voucher cost, probability of passengers to show at a specific time and date, and the number of seats per aircraft.

<!-- /wp:paragraph -->

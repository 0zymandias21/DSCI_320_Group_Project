# **Overview**
**Audience**

This project is meant for anyone trying to understand how countries balance economic growth, environmental responsibility, and social development. Students can use it to explore global patterns, researchers can dig deeper into the forces shaping sustainable progress, policymakers can connect these insights to real decisions, and advocates can use the findings to push for evidence-based change. The dashboard is designed for people who want to look beyond a single statistic and instead explore how different pieces of development fit together.

**Dataset**

To build this project, we brought together three major datasets that each highlight a different side of global development. The first came from Our World in Data and focuses on how countries produce and consume energy. It shows the mix of fossil fuels, nuclear, and renewables, as well as energy intensity and the share of cleaner sources. Because this dataset is carefully standardized, it allows us to fairly compare countries and trace their progress toward sustainability.The second dataset adds an economic layer, covering national gold and currency reserves sourced from central banks and organizations like the IMF. These reserves say a lot about a country’s financial resilience: how well it can handle economic shocks, support infrastructure, and still move toward cleaner energy even when global conditions are unstable.Finally, we used social indicators from Gapminder, including CO₂ emissions per person and women’s years of schooling. These measures bring in the human side of development and help us connect environmental impact with social opportunity. Once the three datasets were cleaned, aligned, and merged, we ended up with a resource that captures energy systems, financial stability, and human development all in one place.

**General Takeaways**

Bringing these datasets together allowed us to ask bigger and more interesting questions than any one dataset could support on its own. Users can explore whether countries with stronger financial reserves are better positioned to invest in clean energy, whether higher education levels relate to lower emissions or more sustainable choices, and whether efficiency really translates into meaningful environmental improvements. They can also compare how income levels or electricity mixes shape emissions, and why some countries with similar economies end up with very different environmental footprints.The bigger lesson from this project is that sustainable development is not driven by a single factor. Energy use, financial capacity, and social progress influence one another in subtle but important ways. By building this integrated dashboard, we hope to give users a clearer view of how these forces interact, and to show that behind every metric is a story about national choices, constraints, and the possibility of a more sustainable future.



# **Waasay Hussain**

## **Theme Statement**

**Emission Patterns:** In this analysis, I develop visualizations that allow users to examine how a country’s energy efficiency (the energy required per unit of GDP) relates to its per-capita CO₂ emissions, and whether this relationship is shaped more by income level or reliance on fossil-based electricity. These visuals are designed to help users assess whether countries that use energy more efficiently actually emit less CO₂ per person, and how much that link depends on economic context or electricity mix. They also allow users to investigate how shifts toward low-carbon electricity affect national emissions overall and identify countries that stand out for better or worse.

## **Advanced Data Wrangling**

**View 1 – Advanced Data Wrangling**

  For View 1, the genuinely advanced wrangling comes from creating new variables that allow users to interpret electricity-mix patterns more clearly. I combined the coal, gas, and oil electricity shares into a single fossil\_share\_elec variable, giving each country one consolidated measure of fossil dependence. I then used binning to convert this continuous percentage into a categorical fossil\_dependency\_group with intuitive labels like Low, Medium, High, and Very High. These engineered variables reshape the dataset in a way that supports clearer grouping and comparison in the visualization. Afterward, I removed incomplete rows and converted the year values to strings so they could be displayed cleanly in the interface.

**View 2 – Advanced Data Wrangling**

  View 2 involves less complex manipulation, but the one step that does qualify as advanced is the creation of a single-year snapshot for each country. By sorting all observations in descending order by year and then dropping duplicates based on country, I ensure that each country is represented only by its most recent complete record. This avoids mixing older and newer data and enables a fair cross-sectional comparison of energy efficiency and per-capita emissions. The remaining cleaning steps: type conversion, column selection, and removing the “World” aggregate, support this structure but are standard rather than advanced.

## **View I: Efficiency vs. Emissions & Fuel Mix Analysis**

**Questions and Low-Level Tasks**

**Analytic Question 1:** Do countries that use energy more efficiently, meaning they use less energy for each unit of GDP, actually emit less CO2 per person? And how much does this link depend on a country's income level or electricity sources?

  The dashboard supports a sequence of low level analytic tasks that help the user understand how energy efficiency, emissions, and electricity composition relate to one another. A central task is to correlate efficiency with emissions. The Efficiency and CO₂ Scatter Plot positions energy use per unit of GDP against emissions per person, making it straightforward to assess whether more efficient countries tend to emit less. Coloring each point by income group adds another dimension, allowing the user to see how economic context shapes the overall pattern.While examining these relationships, the user is encouraged to identify anomalies. Some countries may appear efficient yet exhibit high emissions, while others use more energy but produce fewer emissions than expected. These cases prompt exploration of electricity source makeup or broader economic structures. The filter task is supported by the region and year selectors, which enable the user to narrow the scope of the analysis and see whether observed relationships hold across different regions or time periods.The Fossil Dependency and Income Group Box Plot enables the user to summarize and compare how emissions vary across different levels of fossil fuel reliance. By grouping countries into dependency categories and applying a logarithmic scale, the box plot reveals differences in central tendencies and spreads that would be difficult to see otherwise. This provides a distribution based complement to the scatter plot.The view also supports partitioning through income group color and fossil dependency categories, helping the user interpret global patterns more clearly. Finally, the linked Electricity Source Breakdown chart provides details on demand. When the user brushes a selection in the scatter plot, the stacked bar chart shows the full electricity mix for that subset. This connection helps explain why certain clusters appear and clarifies structural factors behind them. Together, these tasks guide the user from broad visual patterns to deeper insight into how economic status, efficiency, and electricity composition shape national emissions.

### 

### **View**

![View I: Efficiency vs Emissions](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/main/images/waasayview1part1.png)
![](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/main/images/waasayview1part2correctedfinal.png)

## **Marks and Channels**

**Viz 1: Energy Efficiency vs  CO2 per Capita Scatter Plot**

  The scatter plot uses point marks to represent individual countries, creating a clear and interpretable space for examining the link between energy efficiency and emissions. The horizontal position encodes energy use per unit of GDP, while the vertical position encodes emissions per person. These two quantitative axes form the foundation for users to evaluate whether more efficient countries also tend to emit less. The choice of position channels for these variables is intentional, since position is one of the most perceptually accurate encodings for supporting correlational analysis.Color is used to encode income group, which introduces a meaningful categorical dimension. This choice allows users to observe how countries at similar economic stages align within the efficiency–emissions relationship and whether particular income groups form recognizable clusters or deviate from expected patterns. Size is reserved for highlighting a country selected through clicking, allowing the visual system to reinforce focus on a single case without interfering with the primary encodings. Opacity also changes when the shared brush is active, helping distinguish selected regions of the plot while maintaining the visibility of the broader dataset.Together, these channels create a rich analytic environment in which users can assess broad trends, inspect anomalies, and interpret how economic context influences the relationship between efficiency and emissions.

**Viz 2: Energy Source  Breakdown Bar Chart**

  The Electricity Source Breakdown chart uses stacked bar marks to display the composition of each selected country’s electricity mix. This chart encodes the five major electricity sources along the horizontal axis as their proportional contributions to a complete one hundred percent. Using stacked bars is effective for revealing the part to whole structure of the energy system, allowing users to see at a glance how much each country relies on coal, gas, oil, nuclear power, and renewables.Color distinguishes each electricity source using a carefully chosen palette that separates fossil fuels, nuclear power, and renewable energy. This color encoding is essential for readability because the stacked format relies heavily on the visual clarity of each segment. The vertical position identifies countries, ordered by the sum of their electricity shares within the brushed selection, which helps highlight those with heavily weighted energy profiles.Opacity plays a secondary role for interactive highlighting. When a country is clicked in the scatter plot, its bar becomes more prominent in this chart, reinforcing the details on demand connection and improving the user’s ability to trace information across the two views.

**Viz 3: Fossil Dependency and Income Group Box Plot**

  The box plot uses standard box plot marks to summarize the distribution of emissions per person across categories of fossil fuel dependency. The horizontal position encodes the fossil dependency group, which divides countries into four ranges based on the share of electricity generated from fossil sources. This categorical division serves as an effective partitioning mechanism to compare how emissions vary under different structural energy conditions.The vertical position encodes emissions per person on a logarithmic scale. This decision addresses the wide variation and heavy right skew of emissions data, making distributional differences and central tendencies far more interpretable than they would be on a linear scale. Color again represents income group, reinforcing the link to the scatter plot and enabling users to situate distributional patterns within economic context.The combination of these channels allows the box plot to function as a summary view that complements the scatter plot, providing a higher level perspective on how dependency on fossil fuels interacts with income status to shape emissions outcomes.

## **Describe the Interaction and Characteristics**

  The interactive structure of this view is designed to support both broad contextual exploration and focused, detail oriented investigation. Each of the three charts responds to a combination of indirect and direct manipulation techniques, creating a coordinated environment in which users can examine efficiency, emissions, and energy composition as interconnected elements of national energy systems.Indirect manipulation is provided through the region and year selectors, which serve as global filters across all charts. Changing the region restricts the analysis to a specific geographic area, while selecting a year limits the dataset to a single point in time. Together, these controls allow the user to frame the analysis within a meaningful temporal and spatial context, making it possible to examine whether patterns in energy efficiency and emissions hold across continents or vary across different periods. Because these filters apply simultaneously to the scatter plot, the box plot, and the electricity source breakdown chart, they maintain a coherent analytical scope across the entire dashboard.Direct manipulation begins with the shared brush in the Efficiency and CO₂ Scatter Plot. By dragging across a specific part of the plot, the user selects a subset of countries that immediately populate the Electricity Source Breakdown chart. This brushing technique encourages exploratory reasoning: once a cluster or visual pattern becomes interesting, the user can investigate its underlying electricity structures with a single gesture. The brush also influences the scatter plot itself by adjusting opacity, which creates a visual distinction between selected and unselected countries without removing the broader context.The scatter plot also supports single point clicking for closer examination of a particular country. When a user clicks a point, that country enlarges and receives a clear outline. At the same time, the corresponding bar in the Electricity Source Breakdown chart gains prominence, allowing the user to locate and study that country’s energy profile with precision. This interaction helps bridge the gap between pattern level observations and country specific detail.The Electricity Source Breakdown chart contributes to this two way relationship by highlighting the clicked country while still preserving the full structure of the brushed selection. This creates a smooth analytic rhythm in which the user can move from a broad subset, to a single selected country, and then back out to interpret the group as a whole.Finally, the Fossil Dependency and Income Group Box Plot remains fully responsive to the region and year selectors. While it does not participate in the brush and click cycle, it provides a stable reference point for distributional comparison across fossil dependency categories. The user can therefore transition between interactive detail in the scatter plot and broader structural insight in the box plot without losing analytic continuity.Together, these interactions create a balanced experience. The global filters anchor the analysis, the brushing mechanism encourages exploratory grouping, and the point clicking feature enables precise inspection. The interplay among the three charts supports a continuous cycle of discovery and verification, aligning directly with the analytical reasoning required for addressing the relationship between efficiency, emissions, and electricity mix.

## **Critique the View**

The set of visualizations in this view offers a strong foundation for examining how national energy efficiency relates to emissions per person and how this relationship shifts across income groups and electricity compositions. The combination of the Efficiency and CO₂ Scatter Plot, the Fossil Dependency and Income Group Box Plot, and the Electricity Source Breakdown chart is particularly well suited to the analytic question because each view adds a distinct perspective that supports deeper reasoning. The scatter plot provides a clear and precise space for assessing the efficiency–emissions relationship through position encodings, while the income group color scheme introduces an economic dimension that helps users identify structural differences across development levels. The region and year selectors strengthen this analysis by situating patterns within meaningful geographic and temporal frames, allowing the user to decide whether the patterns they see are globally consistent or specific to a particular world region or moment in time.The box plot adds further value by offering a distribution based perspective on emissions across different levels of fossil dependency. The logarithmic scale is especially important, as it preserves interpretability across countries with very small or very large emissions values. The Electricity Source Breakdown chart then ties everything together by linking clusters in the scatter plot to their underlying electricity mixes, creating a bridge between observed patterns and the structural energy conditions behind them. This helps users move beyond surface level associations and understand the energy profiles driving particular outcomes.Even with these strengths, there are areas where refinement could make the view more accessible. Overlapping points in the scatter plot can obscure smaller countries, especially when values cluster closely. Minor opacity adjustments or slight jitter could address this without compromising the meaning of the encodings. The interaction between brushing and clicking, although powerful, may also introduce ambiguity since brushing selects groups while clicking highlights individual cases. A stronger visual cue for clicked countries would clarify this relationship, particularly in the breakdown chart. Finally, the shift from income group colors in the scatter plot and box plot to energy type colors in the breakdown chart requires a moment of cognitive adjustment. This transition is appropriate for the task but could be softened through more prominent legends or subtle visual reminders.Overall, the view demonstrates strong expressiveness, thoughtful separation of variables, and consistent filtering behavior. With small improvements to interaction clarity and visual differentiation, it could become even more intuitive while continuing to support rich, multilayered analysis.

## **View II: Grid Decarbonization vs. Overall Footprint**

### **Questions and Low-Level Tasks**

**Analytic Question 2:** What happens to a country's electricity emissions, and its overall greenhouse gas footprint when it leans into low-carbon energy sources? And which countries stand out for better or worse?

  Within this paired-view design, several key analytic tasks emerge that help users interpret how electricity decarbonization relates to broader emissions outcomes. The bubble chart first enables users to correlate a country’s share of renewable and nuclear electricity with its carbon\_intensity\_elec. The log-scaled y-axis preserves variation across both low- and high-emitting systems, making it easier to discern whether higher low-carbon shares consistently align with cleaner grids.As users consider this relationship, the visualization also draws attention to anomalies, countries whose positions diverge from the expected trend, such as those with substantial low-carbon electricity but elevated grid intensity or disproportionately high CO₂ per capita. These cases highlight deeper structural factors that may influence emissions beyond electricity generation alone.The view further supports comparison across countries by using bubble size and aligned axes to show how similar electricity mixes can lead to different national footprints. Filter controls allow users to partition the dataset by income group, region, or low-carbon thresholds, refining the analysis and revealing more coherent subgroup patterns.Finally, direct selection enables users to retrieve details on demand, linking bubbles to their ranked bar-chart entries and providing exact values. This progression, from correlation to anomaly detection, comparison, partitioning, and detailed confirmation, encourages a clear and systematic interpretation of global decarbonization dynamics.

### 

### **View 2**

![View II: Grid Decarbonization vs. Emissions](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/main/images/waasayview2.png)

## **Marks and Channels**

**Viz 1: Bubble Chart – Grid Decarbonization and Carbon Intensity**

  The first visualization uses a bubble chart to position each country within a two-dimensional space that captures both its reliance on low-carbon electricity and the resulting cleanliness of its power system. Circle marks represent individual countries, providing a familiar and interpretable visual unit. The horizontal position encodes the variable low\_carbon\_share\_elec, expressed as the percentage of electricity generated from renewable and nuclear sources. This axis runs from zero to one hundred and directly reflects the degree to which a country has embraced low-carbon power.The vertical position encodes carbon\_intensity\_elec and applies a logarithmic scale. This design choice ensures that variation is visible across the full spectrum of countries, from those with exceptionally low grid emissions to those still dependent on carbon-intensive fuels. Without the log transformation, cleaner countries would cluster almost indistinguishably along the bottom of the chart, masking meaningful differences.Bubble size is tied to co2\_per\_capita, allowing national emissions footprints to become an integral visual dimension rather than an afterthought. Larger bubbles stand out immediately and encourage questions about why certain countries carry substantial per-capita emissions even when their grids appear relatively clean. Color further distinguishes countries by region, helping viewers perceive broad geographic patterns or regional clusters that may arise organically from the data.Altogether, the mark and channel choices in this chart create a layered visual environment in which users can simultaneously evaluate decarbonization levels, grid performance, and national emissions outcomes.

**Viz 2: Bar Chart – Ranking CO₂ Emissions per Capita**

  The second visualization presents a bar chart that ranks countries by their co2\_per\_capita values. Bar marks are well suited for this task because they provide a direct and easily interpretable comparison of magnitude across categories. Each bar corresponds to a single country and is positioned along a vertical, nominal axis sorted from the highest to the lowest per-capita emitter. This sorting immediately reveals where each country stands within the filtered subset and supports rapid ranking and comparison tasks.The horizontal axis encodes co2\_per\_capita quantitatively, with bar length directly representing the magnitude of emissions. Because this measure is central to understanding national climate impact, encoding it through bar length ensures that differences remain both precise and visually intuitive.Color serves as an additional channel, mapping low\_carbon\_share\_elec onto a continuous heatmap scale. This allows viewers to make quick visual associations between a country's progress in electricity decarbonization and its overall emissions ranking. When a user selects a country, the corresponding bar shifts to a dark red highlight, overriding the original color encoding to emphasize the selected item without losing contextual meaning.A text annotation appears alongside the selected bar to present the exact co2\_per\_capita value, supporting accurate interpretation at moments when numerical precision matters. By pairing quantitative encoding with selective textual reinforcement, the chart maintains clarity while still offering detail when requested by the user.Taken together, the marks and channels in this bar chart create a coherent and analytically focused view of national emissions performance, complementing the more structurally oriented insights offered by the bubble chart.

## **Describe the Interaction and Characteristics**

  The dashboard brings together several layers of interaction that make it possible to move fluidly between broad patterns and specific country-level insights. Both the Grid Decarbonization and Carbon Intensity bubble chart and the CO₂ Emissions per Capita ranking bar chart respond to the same set of filters, allowing users to shape the dataset in ways that align with their analytical goals.Indirect manipulation is primarily handled through three interface widgets. The low-carbon slider allows users to raise the minimum threshold of low\_carbon\_share\_elec, immediately focusing the analysis on countries that have made more substantial progress in decarbonizing their electricity sectors. The income group dropdown provides another dimension of refinement by enabling comparisons within economically similar groups, making it easier to observe how development level intersects with energy transitions. The region checkboxes complement this by letting users include or exclude entire continents, which is particularly helpful when exploring geographically coherent trends or when trying to isolate regional exceptions. Together, these filters give the user a great deal of control over the analytical frame, making the dashboard adaptable to a wide range of investigative approaches.Direct manipulation adds a more immediate and engaging layer to this structure. In the bubble chart, users can click any country to highlight it, which then triggers a corresponding highlight in the bar chart. The selected bar appears in dark red and displays its exact co2\_per\_capita value, making it easy to connect a country’s position in the low-carbon versus carbon-intensity space with its overall emissions footprint. This direct linkage encourages users to follow their curiosity: a surprising bubble in the scatterplot becomes an instant reference point in the emissions ranking. The bubble chart also supports zooming and panning, which is especially useful in regions where many countries cluster closely together. By allowing users to examine these dense areas more carefully, the chart accommodates both global and fine-grained comparisons within the same interactive space.Overall, the combination of filtering, clicking, and scale-based navigation creates a cohesive and intuitive workflow. Users can begin with a broad pattern, narrow the context through filters, isolate an intriguing case through selection, and then retrieve precise details without ever breaking the flow of analysis. This interactive structure strengthens the dashboard’s ability to reveal how different electricity pathways shape national emissions outcomes.

## **Critique the View**

  The paired view dashboard is well suited for examining the relationship between electricity sector decarbonization and national emissions outcomes. By positioning the Grid Decarbonization and Carbon Intensity bubble chart beside the CO₂ Emissions per Capita ranking bar chart, the design creates a unified analytical environment where users can move naturally between structural electricity patterns and the broader emissions impacts they produce. This pairing directly supports the analytic question by allowing users to observe how shifts in electricity generation appear in grid intensity values and how these changes connect to per-person emissions. Synchronized filters across both charts reinforce coherence by ensuring that the two views always display a consistent subset of countries.A major strength of the dashboard lies in the expressive power of the bubble chart. Mapping countries by their share of low carbon electricity and grid carbon intensity offers a rich space for interpreting decarbonization trajectories, and the logarithmic vertical axis preserves meaningful variation across very clean and very carbon intensive grids. Bubble size adds an important layer by representing emissions per person, prompting users to consider how electricity patterns translate into national footprints. Region-based color assignments introduce geographic context and highlight regional distinctions.The bar chart complements this depth by providing a direct ranking of CO₂ emissions per person. Its sorted structure makes comparison intuitive, and the color encoding based on low carbon electricity strengthens the conceptual link to the bubble chart. When a user selects a country in the bubble chart, the corresponding bar is highlighted and labeled, supporting focused inspection without losing the broader ranking view.There are still areas where the design can be refined. Visual overlap in the bubble chart sometimes obscures smaller countries, especially where many fall within similar ranges; additional visibility techniques could help. Interaction symmetry is another point for improvement. Currently, selection flows only from the bubble chart to the bar chart. Enabling the reverse flow would create a more complete and intuitive interaction loop. Although the logarithmic axis is appropriate, some users may find it unfamiliar, so a brief annotation could improve accessibility.From a visualization principles standpoint, the dashboard demonstrates strong effectiveness, consistency, and thoughtful redundancy. The logarithmic scale enhances discriminability, the shared filtering system maintains coherence across views, and the repeated emphasis on low carbon electricity supports interpretation from multiple angles. With small adjustments to symmetry and visibility, the dashboard could become even more intuitive while preserving its analytical depth.

## **Individual Summary**

  Working on this project showed me both the appeal and the difficulty of the theme I chose. Exploring how efficiency, electricity mix, and emissions interact felt like a strong direction, but the dataset made the process more challenging than I expected. Many countries had inconsistent reporting, missing values, or full years with incomplete records, which limited how confidently I could analyze change over time. This is what pushed me toward using dropdown boxes for the year. It kept the views clean, but it also meant that users can only examine one moment at a time, making broader temporal patterns harder to identify.These data limitations shaped both views in meaningful ways. In View I, the uneven availability of early data created imbalances in which countries appeared, so the brushing and linking interactions became essential. They helped isolate clusters and make sense of relationships even when the underlying data felt patchy. In View II, the gaps were even more noticeable, especially in the low carbon electricity variables. This influenced why I relied so heavily on the click to highlight mechanism and a simplified filtering design. Without those, the unevenness of the dataset would have been more distracting than informative, and the link between decarbonization and emissions would have been much harder to follow.The part of the project that taught me the most was learning how to adapt my design goals to the constraints of real data. I entered with the hope of identifying clear long term patterns, but the data forced me to rethink how the views should function and what kinds of insights were realistically achievable. This led me to focus on clarity, interpretability, and meaningful interaction rather than overpromising conclusions the data could not support. I also gained a better sense of how different visualization techniques compensate for missing information, how interaction design can guide users toward reliable parts of the dataset, and how careful critique strengthens the final product. The end result feels honest about what the data can show, while still giving users a rich environment for exploring the relationships that do exist.I would definitely like to spend even more time on these vizzes because I feel like I could definitely show more trends with the same data, for example with the first view creating a scatterplot faceted by region, which allowed you to have buttos for each type of energy source, and a year slider would allow me to uncover so many more trends, and this was an initail idea, however coding it was too advanced for my current skill level, and therefore i made a decision for an altenate viz.

# **Manan Shah**

## **Theme: Reliance on Reserves**

This theme investigates how nations rely on gold as part of their total reserves and whether this reliance reflects differences in regional stability, income group, or macroeconomic strategy. The goal is to understand how the composition of reserves (with and without gold) signals a country's standing in socio-economic metrics.

Beyond understanding how gold shapes financial portfolios, the broader purpose of this project is to connect economic strength with social development. By examining total reserves alongside indicators such as life expectancy, education, access to electricity, and GDP per capita, this analysis explores how financial capacity translates into well-being and equality. The project aims to uncover whether wealth accumulation through reserves leads to tangible social improvements or whether disparities in income and access persist despite economic growth. Through this investigation, I hope to highlight the nuanced relationship between a nation’s financial resilience and its ability to sustain inclusive, long-term development.
## **Advanced Data Wrangling**
For the most part, I had done all data wrangling required beforehand. All that was left was creating a couple of columns that would be vital for my final views. These included:
- `gold_share`: the proportion of gold in a nation’s total reserves.  
  ![gold_share](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/12538884acd9bb08a6e8f17424da81339cb5ee60/images/image_2025-12-04_173954252.png)

- `education_index`: the average years of schooling between men and women.  
  ![education_index](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/12538884acd9bb08a6e8f17424da81339cb5ee60/images/image_2025-12-04_174021025.png)

- `social_index`: blend of normalized scores for 3 social factors: Education Index, Access to Electricity and Life Expectancy
  ![social_index](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/12538884acd9bb08a6e8f17424da81339cb5ee60/images/image_2025-12-04_174041545.png)

As well as the log of my Gold and Reserves variables `gold_share_log`, `log_reserves_gold` and `log_reserves_no_gold` so that my visualizations are clear and easier to interpret patterns from. 

`social_index` was definitely the most challenging one to make. I created a for loop and then iterated through the variables above, applying the normalizing formula and then eventually finding the mean of the 3 scores. 

## **View I**

![View I: Gold Share: Distribution, Comparison, and Trends](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/df40b79bdb47ba3e2bf3d372b9879aacdcad0a21/images/MananView1.png)
### **Analytical Question and Low-level Tasks**

#### Analytical Question: *How does the proportion of gold in total reserves differ across countries and regions and what is the relationship between gold-share and income groups?*
#### Task Abstraction:
1. **Compute Derived Value**: What is the proportion of gold in total reserves across countries? (Gold Share)
2. **Charactize Distribution**: How is gold-share distributed across income groups?
3. **Compare**: Are there trends in gold-share between low income and high income countries?

### **View I: Visualization and Channel Characteristics**

#### Visualization 1.1: Density Plot by Region and Income Group
This chart uses the **Area mark** (configured as a set of violin plots) to represent the statistical distribution of **Log Gold Share**  on the Y-axis across different regions and income groups. The **Column channel** facets the plot by **Region**, allowing quick comparative analysis. The **Color channel** is used to encode the categorical variable **Income Group** (`Low` to `High`), showing how gold share density patterns differ between income levels within each geographical area. The design effectively manages the data's inherent skew and serves as the interactive source for regional selection.

#### Visualization 1.2: Country Gold Share Bar Chart (Filtered by Region)
This visualization uses the **Bar mark** to accurately display the **Gold Share (%)** (X-axis) for individual countries (Y-axis). This view acts as a detail-on-demand component, as it is dynamically **filtered** by the **Region** selected in Visualization 1.1. Its primary interactive role is to allow the audience to click a country bar, setting the `country_select` parameter which then drives the trend analysis in Visualization 1.4.

#### Visualization 1.3: World Average Gold Share by Income Group
This is an **Advanced Visualization** constructed by **layering** two distinct marks: the **Point mark** showing the mean gold share and the **Error Bar mark** showing the standard deviation. The X-axis categorizes the **Income Group**, while the Y-axis plots the **Average Gold Share**. This combination allows for a sophisticated comparison of both the central tendency (mean) and the dispersion (variability) of gold holdings across income levels. The chart is filtered dynamically by clicking the legend, allowing the user to exclude specific income groups from the statistical summary. This also directly answers Analytical Tasks 2 and 3 as it not only allows us to visually see the disparity between groups but the filter ability allows us to compare the low income and high income countries. 

#### Visualization 1.4: Gold Share Trend for Selected Country
This chart uses the **Line mark** with visible **Points** to track the time-series change in **Gold Share (%)** (Y-axis) from 2005 to 2015 (X-axis, treated as Ordinal). The **Color** channel maintains consistency by encoding the country's **Income Group**. The visualization's content is entirely dependent on the `country_select` filter propagated from Visualization 1.2, providing the necessary decade-long historical trend for the chosen country.

### **View I: Interaction Characteristics**

#### What interactions are available?

View I uses four distinct interactions:

1. **Year Slider (`slider_selection`):** An Indirect Manipulation Interaction (IMI) used for global time filtering (2005–2015).

2. **Income Group Legend Selection (`income_group_select`):** An IMI that toggles the visibility of different income groups in Viz 1.3 (Error Bar Chart).

3. **Region Click Selection (`region_select`):** A Direct Manipulation Interaction (DMI) on the density plots (Viz 1.1) to populate Viz 1.2 with countries in the selected region

4. **Country Click Selection (`country_select`):** A DMI on the bar chart (Viz 1.2) to select a specific country for Viz 1.4.

#### Why those interaction types?
* **Sliders (IMI):** Used for the **Year** variable because time is an ordered, quantitative domain. The slider provides quick, precise control over the continuous range of years, suitable for the **Filter** task without requiring typing.

* **Legend Selection (IMI):** Used for **Income Group** because it is a categorical variable. This allows the audience to instantly **Filter** (data) by including or excluding entire categories from the statistical summary (Visualization 1.3), supporting quick comparison of means and standard deviations.

* **Click Selection (DMI):** Used for **Region** and **Country** because it supports a chained drill-down pattern. Clicking a mark directly in the source visualization (1.1 or 1.2) is intuitive for the **Select** and subsequent **Filter** task, immediately linking the user's focus to the detail views. Opacity encoding provides direct visual feedback that the selection is active and makes it easier for the user to understand what is being displayed.

#### How do they support the tasks?

The interactions support the view's analytical question by enabling a cohesive **Filter** and **Details-on-Demand** strategy:

* **Global Filtering:** The **Year Slider** globally supports the low-level task of **Filter** (data) by income-groups, ensuring that all comparisons (regions, countries, and income groups) are based on the same temporal snapshot.

* **Regional Drill-Down:** The **Region Click Selection** (DMI) supports **Select** (item) and **Filter** (data) by focusing the high-level density plots (1.1) to display countries in the filtered bar chart (1.2), answering *How does gold share differ across countries in a specific region?* as it provides a visual representation of gold shares across regions and allows us to drill down into said regions to see which countries are attributing to the stats.

* **Year Slider:** The Year Slider doesn't actually answer any of the analytical tasks as they are done by other Vizzes. However, this feature does allow us to find patterns in time trends and allows the user to gain more insight of how gold shares have changed over the years for countries. 

### **View I: Critique**

#### **Strengths**

1. **Effective Sequencing (Filter/Detail):** The dashboard structure follows the principle of "Overview first, zoom and filter, then details on demand." The flow from regional density (V1.1) to country ranking (V1.2) to income group summary (V1.3) and finally to historical trend (V1.4) guides the user logically through the analysis of distribution and comparison.

2. **Clear Coordination:** The cross-filtering between V1.1 (Region) and V1.2 (Countries) is strong, allowing the user to drill down and immediately answer the question of how gold share is distributed within a specific geographical area. The interaction is intuitive and enhances data exploration significantly.

3. **Appropriate Time Series Visualization:** V1.4 (Line Chart) correctly uses a standard and highly readable method for displaying the **trends** (Task 3) for the selected country, supporting high-precision value retrieval over time.

#### **Weaknesses and Suggestions for Improvement**

1. **Inconsistent Distribution Encoding (Task 2):**

   * **Critique:** Task 2 asks to **Characterize Distribution** of gold-share across income groups. While V1.1 uses the most effective method, a **Violin/Density Plot**, to show the *regional* distribution, V1.3 switches to a less informative **Error Bar Chart** for the *income group* distribution. The error bar only shows the mean and standard deviation (or range), obscuring multi-modal distributions (e.g., if "High Income" countries cluster at 5% and 20% gold share).

   * **Suggestion:** Replace V1.3 (Error Bar Chart) with a **Violin Plot** (similar to V1.1) grouped by Income Group. This would allow a direct visual comparison of the full density shapes, fulfilling the **Charactize Distribution** task more completely.

2. **Labeling and Annotation:**

   * **Critique:** While the overall axis labeling is present, the axes on V1.1 (Density Plots) are not explicitly labeled, forcing the user to infer the X-axis (`Gold Share (%)`) from V1.2. In a final deliverable, the axis labels should be consistent and clear across all four charts, even when the variable is the same. The graphs could also be slightly cleaner if a lot of the ink was removed.

   * **Suggestion:** Ensure all X and Y axes are explicitly labeled, including units (e.g., "Gold Share (%)").

3. **Ambiguous Y-Axis in V1.1:**

   * **Critique:** In V1.1 (Density Plots), the Y-axis (height of the violin/density curve) represents probability density, but this is unlabeled and typically serves no analytical purpose other than defining the shape. Including the Y-axis grid lines adds non-data ink (Tufte's data-ink ratio concept) without aiding the primary task of comparing distribution shapes.

   * **Suggestion:** Remove the Y-axis and any corresponding grid lines from V1.1 to increase the data-ink ratio and reduce visual clutter, focusing the user purely on the density curves and their position on the Gold Share axis.

View I is a highly functional and well-coordinated dashboard that successfully employs the filter-detail pattern for exploration. It excels at showing country-level ranking (V1.2) and temporal trends (V1.4). However, it weakens its execution of **Task 2 (Charactize Distribution)** by using a summary chart (V1.3) when a full distribution chart (like V1.1) would be more appropriate for revealing the true shape of the gold share data across income groups. A simple replacement of V1.3 with a violin plot would significantly enhance the view's analytical power.

## **View II**

![View II: Reserves and Social Development](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/df40b79bdb47ba3e2bf3d372b9879aacdcad0a21/images/MananView2.png)
### Analytical Question and Low-level Tasks

#### **Analytical Question 2: To what extent does a nation’s total reserves relate to social well-being indicators such as life expectancy, education metrics, access to electricity, and GDP per capita?**
#### Task Abstraction: 
1. **Correlate**: What are the relationships between total reserves and social well-being indicators?
2. **Compute Derived Value**: What is the average years in school (education index) in each country?
3. **Compute Derived Value**: What is the blended score of countries consisting of social factors?
4. **Retrieve Value**: What percentage of countries have similar education metrics between men and women?

### **View 2: Visualization and Channel Characteristics**

#### Visualization 2.1: Total Reserves vs. Social Index (Scatterplot)
This chart uses the Point mark to encode each country’s Total Reserves on the Y-axis and its Social Index score on the X-axis. This design allows users to investigate whether higher social well-being correlates with higher national reserve levels. The Color channel encodes the categorical variable Region, enabling quick geographic comparisons across continents. Size encodes GDP per Capita, adding a third quantitative attribute without obstructing visual clarity. A lightly shaded background band highlights high Social Index values above 0.90, helping the audience easily detect countries that outperform socially. This visualization supports pattern detection and outlier identification across global regions.

#### Visualization 2.2: Gold Share vs. GDP per Capita (Scatterplot)
This visualization also uses the Point mark, plotting Gold Share percentage on the Y-axis against GDP per Capita on the X-axis. Scatterplots are well suited for examining wide variation in economic indicators, making this chart effective for revealing clusters, heterogeneity, and potential nonlinear relationships. The Color channel again encodes Region to maintain consistency with Visualization 2.1 and reinforce comparability across the view. This visualization supports investigative tasks that explore whether wealthier countries hold a larger or smaller proportion of their reserves in gold.

#### Visualization 2.3: Average Years in School by Gender and Country (Stacked Bar Chart)
This chart uses the Bar mark in a stacked configuration to show combined average schooling years for males and females in each country. The Length channel encodes the quantitative value, where longer bars represent higher total schooling years. Color differentiates gender groups, allowing users to compare both total attainment and gender distribution at a glance. Countries are listed along the Y-axis and sorted by total schooling years, enabling rapid comparisons and highlighting disparities in educational outcomes across nations. This visualization offers a social perspective that complements the economic patterns shown in Visualizations 2.1 and 2.2.

### **View 2: Interaction Characteristics**

#### What interactions are available?
View 2 uses three distinct interactions:

1. **Year Slider (`slider_selection2`)**  
   An Indirect Manipulation Interaction that filters all three charts to a selected year between 2005 and 2015.

2. **Interval Brush Selection (`brush_selection`)**  
   A Direct Manipulation Interaction applied on the Reserves vs Social Index scatterplot. Users drag to select a region of the chart based on Social Index (x) and Total Reserves (y). This also serves as my Bi-Directional Interaction as Visualization 2.1 and 2.2 both affect each other based on what is selected on the respective graphs.

3. **Linked Highlighting Across Charts**  
   The brush applied in the first scatterplot propagates to the Gold Share vs GDP chart and the Education stacked bar chart. Selected points retain their original colors, while non selected points become light grey or reduced opacity.

#### Why those interaction types?
**Sliders (IMI):**  
The Year slider is well suited for temporal filtering because time is an ordered, continuous variable. A slider supports quick adjustments without requiring input boxes and allows users to compare multiple time snapshots efficiently. This supports filter tasks at the global time level.

**Interval Brush (DMI):**  
The brush is appropriate because both the Social Index and Total Reserves are quantitative attributes that benefit from freeform selection. Users can physically drag across the plot to isolate a subset of countries, supporting select and filter tasks. Brush outputs are immediately visible and intuitive, making it a natural choice for exploring multivariate clusters.

**Linked Highlighting:**  
Linking color changes across charts reinforces the connection between economic and social indicators. This interaction allows users to understand how a selected subset behaves in the other visualizations, supporting relational comparisons such as how the same countries differ in gold share or educational attainment.

#### How do they support the tasks?
The interactions in View 2 directly support the analytic question by enabling users to explore how a nation’s total reserves relate to several social well being indicators. The year slider and interval brush provide mechanisms for correlating variables, retrieving country level values, and interpreting derived differences across charts.

**Correlate:**  
The interval brush on the Reserves vs Social Index scatterplot allows users to isolate a subset of countries and see how these same countries appear in the Gold Share vs GDP chart and the Education stacked bar chart. This coordinated highlighting supports correlating total reserves with GDP per capita, gold share, and schooling levels, which directly aligns with the analytical question.

**Retrieve Value:**  
Hover tooltips in each visualization provide precise values such as total reserves, social index, gold share, GDP per capita, and average schooling years. Tooltips provided also show the difference between male education and female education in countries. This supports retrieving detailed information for specific countries and comparing them within or outside the brushed selection.

**Compute Derived Value:**  
The stacked bar chart visually encodes the difference between male and female schooling years, which allows users to interpret gender based educational disparities. When combined with brushing, users can evaluate whether high reserve countries tend to show higher or more balanced education outcomes. This helps compute derived interpretations relating to social well being.

**Task Not Supported: Retrieve Value on Percentage Similarity (Task 4):**  
The task that aims to retrieve what percentage of countries have similar education metrics between men and women is not supported by View 2. Although the stacked bar chart allows users to compare male and female schooling years for individual countries, the visualization does not aggregate or quantify how many countries share similar gender parity levels. There is no interaction or summary element that computes or displays the percentage of countries meeting a similarity threshold. This represents a gap in the current design because the view only allows the audience to inspect gender differences at the individual country level, not to perform population level comparisons required for Task 4.

Overall, the interactions in View 2 effectively support correlating reserves with several social indicators, retrieving values, and interpreting derived differences, but the design does not address the population based percentage retrieval required by Task 4.

### **View 2: Critique**

#### Strengths

1. **Coordinated multi view structure for correlation tasks**  
   View 2 is well suited to the core Correlate task. The combination of the Reserves vs Social Index scatterplot, the Gold Share vs GDP scatterplot, and the stacked schooling bar chart allows users to track the same set of countries across multiple indicators. The interval brush consistently propagates selections to the other charts, helping users explore how financial, economic, and social attributes relate across nations.

2. **Appropriate encodings for key variables**  
   All quantitative attributes are encoded using position, which follows perceptual accuracy principles. Social Index, Total Reserves, GDP per capita, Gold Share, and schooling years are displayed in ways that support rapid comparison and meaningful visual interpretation.

3. **Effective use of color and size for additional dimensions**  
   Color encodes Region in both scatterplots and Gender in the stacked bar chart. Size is used for GDP per capita in the first scatterplot. These channels provide additional layers of information without overwhelming the user.

4. **Interactions that meaningfully support exploration**  
   The year slider and brush selection allow users to filter and isolate subsets of interest. This supports exploratory analysis and provides a pathway to answering questions about how reserves correlate with social well being measures.

#### Weaknesses and Suggestions for Improvement

1. **Lack of regression lines limits the ability to assess relationships**  
   Neither scatterplot includes a regression line or any statistical trend cue, which limits the user’s ability to judge the strength, direction, or significance of relationships between variables. For example, it is difficult to tell whether Total Reserves actually increase with Social Index or whether GDP per capita is meaningfully related to Gold Share.  
   **Suggestion:** Adding a regression line with confidence intervals would allow users to more accurately determine whether correlations exist and whether they are strong or weak. This aligns with course principles of supporting analytical tasks with appropriate statistical scaffolding.

2. **Task 4 is not supported by the design**  
   Task 4 asks for the percentage of countries with similar education metrics between men and women. View 2 does not compute or visualize any summary statistic related to gender parity. The stacked bar chart only supports item level comparisons.  
   **Suggestion:** Add a summary indicator or a small chart showing the proportion of countries with small gender differences. This could update dynamically with the brush selection.

3. **Ambiguity in the reserves encoding and axis labeling**  
   The y axis displays `log_reserves_gold` but is labeled simply as Total Reserves. This hides the transformation and may mislead the user about what scale they are interpreting.  
   **Suggestion:** Label the axis explicitly as Log Total Reserves and briefly justify the transformation.

4. **Cognitive load from inconsistent channel use for income**  
   GDP per capita switches from being encoded as size in the first scatterplot to position in the second. Because the meaning of size is not used consistently, users must mentally reassign the variable between charts, increasing cognitive load.  
   **Suggestion:** Use GDP per capita consistently either as an axis or as a size channel across both scatterplots.

5. **Visual clutter in dense scatterplots**  
   The first scatterplot becomes crowded for certain years or regions, making points overlap significantly.  
   **Suggestion:** Reduce default point size, introduce slight jitter, or allow filtering by region in addition to brushing.

6. **Education chart may obscure broader context**  
   The education bar chart fully filters out non brushed countries, which can make it difficult to understand the global schooling distribution and how selected countries compare to the rest.  
   **Suggestion:** Highlight brushed countries rather than filtering entirely, allowing users to retain context while still focusing on the selected group.

#### Overall assessment
View 2 provides a strong foundation for analyzing the relationship between financial reserves and social well being indicators. The coordinated brushing, temporal flexibility, and clear encoding choices support meaningful exploration. However, the absence of regression lines, the lack of support for Task 4, and inconsistent channel assignments limit the view’s analytical depth. Adding regression trends, clearer labeling, and parity summaries would greatly strengthen the interpretability and task alignment of the view.

## **Individual Summary**

Creating these visualizations helped me gain a deeper understanding of coordinated multi view analysis and the challenges of designing dashboards that accurately support analytical tasks. Through building View 1 and View 2, I learned how brushing, linking, and multiple selection parameters work together and how easily interactions can become fragile when several charts depend on the same filters. I also realized the importance of being transparent with transformations, such as the log scaling on reserves, and the need for consistent encoding choices across views. One of the most important insights from the data itself was that my findings were not causal. The large error bars in View 1 revealed wide variation within income groups, including high income countries with both low and high gold shares, emphasizing that reserves and income classifications alone cannot fully explain differences in gold positions.

I faced several challenges throughout the process. Implementing complex interactions often meant that changing one parameter could unintentionally break several other components, making debugging difficult and time consuming. Ensuring that channel assignments were meaningful and consistent required multiple iterations. I had also hoped to include a world map to support geographic interpretation, but creating a global choropleth proved impractical due to limited resources and the additional complexity of formatting geographic data.

If I had more time, I would improve several aspects of my design. I would add regression lines to both scatterplots to better support correlation tasks, introduce clearer axis labels to reduce ambiguity, and add an aggregated summary to support Task 4. I would also pursue the world map idea to enable geographical comparisons, redesign the education chart for clarity, and refine interactions to reduce visual clutter. Overall, this project improved my understanding of multivariate visualization, interactive design, and the level of detail required to translate analytical questions into effective visual tools.

# **Sainzaya Baasankhuu**
## Theme Statement

Theme: Global energy patterns and socioeconomic development

## Advanced Data Wrangling

Explanation of advanced data wrangling (if applicable) (<400)
Most of my wrangling was straightforward (renaming, melting, filling missing values). The most advanced step was ranking countries by renewable share in 2024, which required grouping and ordering within categories. Through this wrangling, I built the Top 10 countries in the renewable source comparison chart.”

## View I: Global Renewable Energy Adoption and Socioeconomic Development
![View I: Global Renewable Energy Adoption and Socioeconomic Development](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/main/analysis/Sainzaya%20Baasankhuu/notebook/View%201.png)
**Questions and Low-Level Tasks**

Main analytic question: How does renewable energy adoption shape socioeconomic development across countries?

Sub-questions:
- What is the relationship between income and life expectancy in countries with different levels of renewable adoption?
- How has the composition of electricity sources (solar, wind, hydro, biofuel, other) changed over time within a selected country?
- Which countries are the top performers in renewable electricity share in the most recent year (2024)?
- How does the selected country’s renewable energy proportion compare to top renewable energy consumers?

Low-level tasks it support (Stasko’s taxonomy):

Identify: Spot countries with high vs. low renewable adoption.

Compare: Contrast socioeconomic outcomes (income, life expectancy) across adoption levels.

Trend: Observe historical changes in electricity source shares over time.

Rank: See the top 10 countries by renewable electricity share in 2024.

Filter/Select: Focus on specific countries or energy sources using interactive selections.

Summarize: Get an overview of global adoption patterns and socioeconomic development links.

## Description of the Visualization and Channels

Marks: 
- Scatter plot: Circles (mark_circle) represent countries in 2018, chosen for clarity and comparability.
- Regression lines: Lines (mark_line) make it easier to see how countries with different renewable adoption levels differ in socioeconomic trends, supporting pattern recognition.
- Stacked area chart: Areas (mark_area) encode electricity source shares over time, emphasizing cumulative contribution.
- Bar chart: Bars (mark_bar) encode renewable share for top 10 countries in 2024, supporting ranking tasks.

Channels: 
- Position (x, y): Used for quantitative variables (income, life expectancy, year, share). Position is the most accurate channel for magnitude comparison.
- Color (hue): Encodes categorical variables (renewable adoption level, energy source). Color is effective for distinguishing categories.
- Opacity: Used to highlight selected countries or categories, reducing clutter and guiding attention.

Characteristics of Channels Exploited: 
- Position: Exploits human ability to compare values precisely along aligned axes (scatter, bar, stacked area).
- Color: Exploits categorical distinction. Adoption levels (High/Medium/Low) and energy sources (Solar, Wind, Hydro, etc.). The energy source's color resembles the real renewable sources so that users intuitively associate the color with that renewable source. For example, solar is encoded as yellow, and hydro is encoded as blue.
- Opacity: Exploits pre-attentive processing to emphasize selected data while de-emphasizing unselected points.
- Direction (line slope): Regression lines exploit slope perception to communicate correlation trends.

## Interactions and Their Characteristics

What interactions are available?: 
- Legend selection: Users can click renewable adoption levels or energy sources to filter the data.
- Bidirectional interaction: Selecting a renewable source in the stacked area chart shows the top 10 countries for that source in the ranking chart. Selecting a country from the top 10 list then reveals that country’s energy composition back in the stacked area chart.
- Country selection: Clicking a country highlights it across all charts.
- Checkbox controls: Toggle regression lines and scatter points on or off.
- Hover tooltips: Provide detailed information (country, year, source, share, socioeconomic values) without cluttering the chart.

Why those interaction types?: 
- Legend selection was chosen because categorical filtering is intuitive and supports comparison across adoption levels or energy sources.
- Bidirectional interaction between stacked area and ranking charts was added to connect macro trends (global adoption by source) with micro insights (top performers and their energy mix). It lets users move fluidly between “which sources dominate globally” and “which countries lead in that source.”
- Country selection enables coordinated multiple views, letting users trace one country’s story across scatter, stacked area, and ranking charts.
- Checkboxes give users control over chart complexity, allowing them to simplify or enrich the scatter plot depending on their analytic needs.
- Tooltips provide detail-on-demand, aligning with Shneiderman’s mantra (“overview first, zoom and filter, then details on demand”).

How do they support the tasks?: 
- They enable identify (highlighting a country), compare (contrasting adoption levels), trend (exploring electricity mix over time), and rank (seeing top performers).
- Bidirectional interaction specifically supports drill-down and roll-up analysis: users can start from a renewable source and discover its leading countries, then pivot to see how those countries compose their energy mix. This reinforces both global and country-level narratives.
- Interactivity reduces cognitive load by letting users focus on subsets of data rather than all countries at once.
- Coordinated highlighting ensures consistency across views, reinforcing the narrative of adoption and socioeconomic outcomes.

## Critique of the View and Suitability

Assess suitability for addressing the tasks

The scatter plot effectively supports comparison and pattern recognition tasks, showing correlations between adoption levels and socioeconomic outcomes.
The stacked area chart is well-suited for trend analysis, showing how electricity sources evolve over time.
The bar chart directly supports ranking tasks, making top performers clear.

What works well?

Use of position channels (x, y) ensures accurate magnitude comparisons.
Color encodes categorical distinctions effectively (adoption levels, energy sources).
Interactivity is examiner-friendly: selections and checkboxes make the dashboard flexible and customizable.
Coordinated multiple views provide a coherent story across different perspectives.

What could be better?

The scatter plot only shows one year (2018), limiting temporal insight into socioeconomic outcomes.
The stacked area chart can become cluttered for countries with overlapping sources, and disabling the legend forces reliance on color memory.
Color palettes should be checked for accessibility (e.g., color-blind users).

Critique based on course principles

The dashboard succeeds in supporting multiple low-level tasks (identify, compare, trend, rank) and aligns with principles of effective encoding (position for quantitative, color for categorical).
Interactivity follows best practices by offering filtering, highlighting, and detail-on-demand.
Limitations are in scope (single-year scatter, clutter in stacked area).

## View II: Energy Mix vs Environmental & Health Impact
![View II: Energy Mix vs Environmental & Health Impact](https://github.com/ubc-dsci320-2025w1/project-team_wmss/blob/main/analysis/Sainzaya%20Baasankhuu/notebook/View%202.png)
**Questions and Low-Level Tasks**

Main analytic question: How does the composition of a region’s electricity mix relate to environmental and health outcomes?

Sub-questions: 
- What is the balance between fossil fuels and renewables across regions in a given year?
- How do CO₂ emissions per capita correlate with child mortality across regions?
- Which regions stand out as having both high fossil fuel reliance and poor health outcomes?
- How does selecting a region reveal its energy mix and associated environmental/health profile?

Low-level tasks it supports (Stasko’s taxonomy): 
- Identify: Spot regions with high fossil fuel share or high renewable share.
- Compare: Contrast energy mixes across regions.
- Trend/Correlation: Observe the relationship between emissions and child mortality.
- Filter/Select: Focus on specific regions or years using interactive selections.
- Summarize: Provide an overview of how energy mix relates to environmental and health indicators.

## Description of the Visualization and Channels

Marks: 
- Heatmap: Rectangles (mark_rect) encode electricity share by region and energy type.
- Scatter plot: Circles (mark_circle) represent countries, positioned by CO₂ emissions per capita and child mortality.

Channels: 
- Position (x, y): Used for quantitative variables (CO₂ emissions, child mortality, region, energy type). Position enables precise comparison.
- Color (intensity/hue): In the heatmap, color intensity encodes the share of electricity (%). In the scatter, color hue encodes region categories.
- Stroke/outline: Used in the heatmap to highlight selected regions.
- Size (scatter): Fixed circle size ensures visibility and comparability.

Characteristics of Channels Exploited: 
- Position: Exploits human ability to compare values along axes (scatter) and categorical grids (heatmap).
- Color intensity: Exploits pre-attentive processing to quickly identify high vs. low shares in the heatmap.
- Color hue: Distinguishes regions in the scatter plot.
- Stroke width: Provides clear highlighting of selected regions in the heatmap.

## Interactions and Their Characteristics

What interactions are available?: 
- Region selection: Clicking a region highlights it across both visualizations.
- Year slider: Adjusts both heatmap and scatter plot to show data for a specific year.
- Hover tooltips: Provide detail-on-demand (country, region, energy type, share, emissions, mortality).

Why those interaction types?:
- Region selection enables coordinated multiple views, letting users trace one or multiple region’s energy mix and its environmental/health outcomes.
- Year slider supports temporal exploration, showing how mixes and outcomes evolve.
- Tooltips provide detail-on-demand without cluttering the visualization.

How do they support the tasks?: 
- Enable identify (highlighting regions with extreme values), compare (contrasting mixes and outcomes), trend/correlation (scatter relationships), and summarize (overview of global patterns).
- Coordinated highlighting ensures consistency across views, reinforcing the narrative of energy mix and impacts.

## Critique of the Visualization

Assess suitability for addressing the tasks

The heatmap effectively supports identification and comparison tasks, showing magnitude patterns across regions and energy types.
The scatter plot supports correlation analysis, showing how emissions relate to child mortality.

What works well?

Position channels ensure accurate magnitude comparisons in the scatter.
Color intensity in the heatmap makes extremes immediately visible.
Interactivity (region selection, year slider, tooltips) makes the visualization examiner-friendly.
Coordinated multiple views provide a coherent story across different perspectives.

What could be better?

Scatter plots may overlap points; jittering or transparency could help.
Color palettes should be checked for accessibility (color-blind users).
Adding regression lines or summary statistics could strengthen correlation analysis.

Critique based on course principles

The visualization succeeds in supporting multiple low-level tasks (identify, compare, trend, correlation) and aligns with principles of effective encoding (position for quantitative, color for categorical/magnitude). Interactivity follows best practices by offering filtering, highlighting, and detail-on-demand. Limitations are in scope (potential clutter in heatmap, overlapping scatter points).

### Individual Summary on Views and Your Theme

Across both dashboards, the theme is understanding how energy adoption and mix connect to broader outcomes: socioeconomic development in one case, and environmental and health impacts in the other.
In the Renewable Adoption and Socioeconomic Development dashboard, the scatter visualization highlighted the relationship between income and life expectancy across adoption levels, supported by regression lines for pattern recognition. The stacked area visualization showed how electricity sources evolved over time within a country, while the bar visualization ranked top performers in renewable share for 2024. Together, these views supported identify, compare, trend, and rank tasks, with coordinated interactions ensuring consistency across perspectives. The limitation was the scatter being restricted to a single year, which constrained temporal analysis.
In the Energy Mix vs Environmental & Health Impact dashboard, the heatmap visualization provided a clear overview of fossil versus renewable shares by region, exploiting color intensity for quick identification. The scatter visualization positioned countries by CO₂ emissions per capita and child mortality, enabling correlation analysis. Interactivity through region selection and year sliders connected the two views, allowing users to trace regional energy mixes and their associated impacts. The main challenge was potential clutter in the heatmap and overlapping points in the scatter, which could obscure finer details.
Overall, both dashboards align with the theme by linking energy choices to human and environmental outcomes. I believe they succeed in supporting multiple low-level tasks through effective use of position, color, and interactivity, though each has scope for refinement in clarity and temporal depth.

## Summary (Group)

Working on these dashboards gave our team a deeper understanding of coordinated multi‑view analysis and the challenges of designing interactive visualizations that remain robust under multiple filters. Through building View I and View II, we learned how brushing, linking, and selection parameters can connect charts meaningfully, but also how fragile interactions become when several views depend on the same inputs. We also recognized the importance of consistent encoding choices and transparency in transformations, such as log scaling, to avoid misleading interpretations.

The dataset itself posed significant challenges. Missing values, inconsistent reporting, and uneven availability across years limited our ability to show long‑term trends. This shaped our design decisions: dropdowns and simplified highlighting were used to keep views interpretable, while brushing and linking helped isolate clusters despite patchy data. These constraints reminded us that our findings were not causal, and wide variation within groups emphasized the need for careful critique rather than overpromising conclusions.

We faced technical hurdles in debugging complex interactions, balancing clarity with detail, and iterating on channel assignments to ensure they were meaningful. Some ideas, such as a global choropleth or faceted scatterplots by region, proved too advanced for our current skill level, but they remain directions we would pursue with more time. Improvements we identified include adding regression lines to scatterplots, clearer axis labels, aggregated summaries, and refined interaction design to reduce clutter.

Overall, the project strengthened our collective understanding of multivariate visualization, interaction design, and the need to adapt goals to the realities of the dataset. It taught us how critique and iteration lead to honest yet engaging tools, and how careful design can guide users toward reliable insights even when data is incomplete.



# **Stallon Pinto**

## **Theme: Visualizing Patterns in Electricity Demand, Self-Sufficiency & Renewable Transition**

This project investigates how countries’ electricity systems evolve under changing demand and transition pressures. The theme is organized around two related questions:

1. **Demand & resilience:** When electricity demand changes, do countries keep up through domestic generation (self-sufficiency), or do they rely on net imports (import reliance)? This matters because high import reliance can increase exposure to cross-border constraints and price shocks, while persistent surpluses can indicate export capacity or structural overproduction.

2. **Demand & transition:** When demand rises, are countries increasing the share of renewables in their electricity mix—and if not, where might this create future risks (emissions lock-in, delayed infrastructure transition, or system stress)?

---

## **Advanced Data Wrangling**

The dataset already contains the integrated energy fields needed for both views, so the notebook wrangling focuses on preparing analysis-ready subsets and deriving metrics that directly support the dashboard tasks.

Key wrangling steps used in **View I** include:

- **Time-window restriction (2000–2024):**  
  The dataset is filtered to **2000–2024** to ensure consistent modern coverage and reduce noise from sparse early records.

- **Region imputation (country-consistent fill):**  
  Missing `region` values are filled using a country-level lookup (earliest known region by year for each country). Remaining nulls are labeled as `"Unknown"`. This prevents countries from disappearing under region filtering and keeps region assignments stable across years.

- **Population cleaning + imputation (for size encoding):**  
  Population is coerced to numeric and filled using a median-based strategy (median population by year, with a global fallback). This ensures the **bubble size channel** remains usable across years even when population entries are missing.

- **Derived metric: Net electricity balance (TWh):**  
  A computed field is created for interpretability and to directly support the “supply vs demand” question:  
  **Net electricity balance (TWh) = electricity_generation − electricity_demand**

- **Log-scale readiness (positive domain enforcement):**  
  Electricity demand spans orders of magnitude across countries. The notebook computes global positive demand bounds to safely use a **log x-axis** and avoid non-positive values breaking the scale.

- **Top importers/exporters extraction:**  
  The import dependence view uses ranking logic to select the **Top 25 importers** and **Top 25 exporters** (based on `net_elec_imports_share_demand`) for the selected year. This keeps the bar chart readable and focused on the most informative extremes.

- **Key-year sampling for trajectories:**  
  For country trajectory overlays, the notebook samples benchmark years (e.g., 2000, 2005, 2010, 2015, 2020, 2024) rather than plotting every year. This reduces clutter while preserving long-term movement in demand–balance space.

---

## **View I: Electricity Demand and Production**

![View I: Electricity Demand and Production](../images/view_1_Stallon_Pinto.png)

### **Analytical Question and Low-level Tasks**

#### Analytical Question: *As electricity demand changes, which countries remain self-sufficient versus becoming reliant on imports, and how does this vary across regions?*

#### Task Abstraction:
1. **Compute Derived Value:** For a given country-year, what is the net electricity balance (generation − demand)?
2. **Compare:** In a selected year, how do countries compare in demand scale and balance (surplus vs deficit)?
3. **Identify Extremes:** Which countries are the strongest net importers/exporters (as % of demand) in a given year?
4. **Filter:** How do these patterns change by region and by year?
5. **Trace Trend / Change:** For a selected country, how has its balance shifted over time as demand changed?

---

### **View I: Visualization and Channel Characteristics**

View I uses two coordinated charts (stacked vertically) that together provide a hybrid perspective: a snapshot comparison for a selected year plus a country trajectory and ranked import dependence.

#### Visualization 1.1: Electricity Supply–Demand Balance by Country (Scatterplot)
This chart uses a **Point mark** to represent each country in the selected year.

- **X (position):** `electricity_demand (TWh)` on a **log scale**, allowing both small and large electricity systems to be visible without compressing low-demand countries.
- **Y (position):** `net electricity balance (TWh)` (generation − demand). A dashed **y=0** reference line separates net surplus from net deficit.
- **Color:** `region`, enabling geographic comparison and supporting region-level filtering while keeping a consistent category encoding.
- **Size:** `population` (filled), providing scale/context without replacing the main analytic variables.
- **Tooltip:** includes country, region, year, demand, generation, balance, and net imports (% of demand) for precise value retrieval.
- **Trajectory overlay (on selection):** when a country is selected, a **Line mark with Points** is drawn at benchmark years (e.g., 2000, 2005, 2010, 2015, 2020, 2024), showing how that country’s position in demand–balance space changes over time. Key-year sampling reduces clutter while preserving long-run movement (toward deficit, toward surplus, or stable).


#### Visualization 1.2: Selected Country Trajectory (Overlay on Scatterplot)
A selected country’s historical path is overlaid using a **Line mark with Points**, plotted at benchmark years (e.g., 2000, 2005, 2010, 2015, 2020, 2024).

- **Encodes change over time** in the same demand–balance space (demand on x, balance on y).
- Sampling to key years reduces visual clutter while still communicating long-run movement (toward deficit, toward surplus, stable).


#### Visualization 1.2: Net Import Dependence (Top Importers and Exporters) (Bar Chart)
This chart uses a **Bar mark** to show extreme cases of import reliance and export strength for the selected year.

- **X (position):** `net_elec_imports_share_demand` (%), centered at **0** with a rule. Positive values indicate net import dependence; negative values indicate net exporting.
- **Y (position):** country names, sorted by import dependence.
- **Color:** `region` (consistent with the scatter), reinforcing geographic context.
- **Background shading:** green-tinted on the exporter side and red-tinted on the importer side to make direction immediately interpretable.
- **Ranking:** the view focuses on Top 25 importers and Top 25 exporters to remain readable and task-aligned.

---

### **View I: Interaction Characteristics**

#### What interactions are available?

View I includes two IMI widgets and coordinated DMI selection:

1. **Year Slider (`year_param`) — IMI:**  
   Filters both the scatter and bar chart to a single year (2000–2024). This enables temporal comparison via scrubbing.

2. **Region Dropdown (`region_param`) — IMI:**  
   Filters the dashboard by region (or “All”), supporting within-region comparisons and reducing clutter for focused analysis.

3. **Country Click Selection (`country_fade`) — DMI (bi-directional highlight):**  
   Clicking a country in either chart highlights the same country in the other chart via opacity changes. This supports “details-on-demand” by letting users find a country in one view and immediately see its placement in the other.

4. **Country Click Selection (`country_strict`) — DMI (trajectory trigger):**  
   Clicking a country in the scatter triggers the trajectory overlay. Importantly, this selection is configured so that **when no country is selected, no trajectory is drawn**, preventing the common failure mode where trajectories appear for all countries.

#### Why those interaction types?

- **Slider (IMI):** Year is ordered and quantitative; a slider supports fast, precise temporal filtering without typing.
- **Dropdown (IMI):** Region is categorical; a dropdown is compact and reduces cognitive load versus multi-select checklists.
- **Click selection (DMI):** Clicking marks is a direct and intuitive way to “pin” a country of interest and propagate that focus across coordinated views.

#### How do they support the tasks?

- **Filter tasks (Year/Region):** allow users to keep comparisons consistent (same year) and meaningful (same regional context).
- **Compare + Identify extremes (linked highlight):** enables fast cross-referencing between “top importers/exporters” and their location in the demand–balance distribution.
- **Trace trend/change (trajectory overlay):** provides a compact time-based explanation for how and why a country ends up as a deficit/importer or surplus/exporter case.

---


### **View I: Critique**

#### **Strengths**
This view is well aligned with the core question because it derives a single interpretable metric—**net balance = generation − demand**—and anchors interpretation with a clear **y=0** reference line to separate surplus from deficit. The **log-scale** demand axis is also appropriate for global comparisons because it keeps both small and large electricity systems readable on the same plot. Interaction design strengthens usability: linked highlighting between the scatter and bar chart helps users quickly locate a country across views, and the trajectory overlay adds longitudinal context without requiring a separate time-series chart. Finally, ranking to top importers/exporters and sampling key years are practical readability tradeoffs that keep the dashboard navigable.

#### **Weaknesses / Limitations**
A major limitation is that balance is not a complete proxy for “self-sufficiency”—a country near zero balance can still rely heavily on trade, so users may over-interpret the scatter without consulting the import chart. Overplotting can still be seen near moderate demand and near-zero balance (especially with population sizing), making some comparisons rely on tooltips or zooms. Lastly, the Top-25 importer/exporter framing is useful for screening, but it can bias attention toward extremes and hide moderate-but-relevant cases.





## **View II: Demand Growth vs. Renewable Transition**

### **Title of View**
**Demand Growth vs. Renewable Transition Pressure**

![View II: Demand Growth vs. Renewable Transition](../images/view_2_Stallon_Pinto.png)

### **Analytical Question and Low-level Tasks**

#### **Analytical Question:**  
*Are countries with rising electricity demand expanding renewable electricity fast enough, and where does misalignment between demand growth and renewable transition create future risk?*

#### **Task Abstraction:**
1. **Compare:** How does electricity demand growth per capita relate to changes in renewable electricity share across countries?
2. **Categorize:** Which countries follow similar transition paths based on demand growth and renewable adoption?
3. **Identify Extremes:** Which countries face the highest “transition pressure” from fast demand growth combined with weak renewable uptake?
4. **Track Trends:** How has renewable electricity share evolved over time for selected countries?

---

### **View II: Visualization and Channel Characteristics**

#### **Visualization 2.1: Demand Growth vs. Renewable Transition (Scatterplot)**
This visualization uses a **Point mark** to compare long-run electricity demand growth against renewable transition progress at the country level.

- **X (position):** `pct_change_demand_pc` (% change in electricity demand per capita, 2000–2023).
- **Y (position):** `pct_point_change_renew` (percentage-point change in renewable electricity share, 2000–2023).
- **Color:** custom **transition class** derived from rotated coordinates in standardized demand–renewable space (e.g., *Renewables Lead*, *Demand Surge, Renewables Lag*).
- **Size:** `population (2023)`, scaled using a square-root transform and minimum floor to preserve visibility.
- **Tooltip:** country, class, demand growth, renewable change, renewable share (2023), and population.

---

#### **Visualization 2.2: Renewables Transition Over Time (Line Chart)**
This visualization uses a **Line mark** to show how renewable electricity share evolves over time for selected countries.

- **X (position):** `year` (2000–2023).
- **Y (position):** `renewables_share_elec (%)`.
- **Color:** `country`, allowing multiple selected countries to be compared simultaneously.
- **Conditional rendering:** the chart remains empty until at least one country is selected in the scatter or bar chart, preventing visual noise.


---

#### **Visualization 2.3: Transition Pressure (Top 15 Bar Chart)**
This chart uses a **Bar mark** to rank countries facing the highest transition pressure.

- **X (position):** `pct_change_demand_pc`, measuring how rapidly electricity demand has grown.
- **Y (position):** `country`, sorted by descending demand growth.
- **Color:** `renew_share_end (2023)` using a sequential blue scale to encode current renewable penetration.
- **Filtering:** restricted to countries with low renewable share or negative renewable change.

---

### **View II: Interaction Characteristics**

#### **What interactions are available?**

View II includes three coordinated interactions:

1. **Class Filter (IMI – Dropdown):**  
   Allows users to filter countries by transition class (e.g., Renewables Lead, Demand Surge).

2. **Country Selection (DMI – Click / Multi-select):**  
   Clicking points in the scatter or bars in the transition pressure chart selects countries and highlights them across all views.

3. **Linked Highlighting and Detail-on-Demand:**  
   Selected countries are emphasized via opacity and stroke changes, and their renewable trajectories appear in the time-series chart.

---

#### **Why these interaction types?**

- **Dropdown (IMI):** Appropriate for categorical filtering when the user wants to explore predefined transition typologies.
- **Click Selection (DMI):** Enables intuitive drill-down from abstract patterns (scatter) to concrete cases (time trends).
- **Linked Views:** Reduce cognitive load by preserving context across multiple representations of the same countries.

---

#### **How do they support the tasks?**

The interactions enable a progression from **comparison → selection → explanation**. Users first compare countries globally, then isolate high-risk or interesting cases, and finally inspect how renewable adoption has evolved over time. This structure supports exploratory analysis while keeping the dashboard interpretable.

---

### **View II: Critique**

#### **Strengths**
This view effectively connects long-run demand growth with renewable transition outcomes using a clear, interpretable scatter layout. The custom rotated classification provides a meaningful typology that goes beyond simple quadrants and captures relative performance. Coordinated interaction between the scatter, bar chart, and time-series view supports focused exploration without overwhelming the user. Conditional rendering of trend lines is especially effective in reducing clutter.

#### **Weaknesses / Limitations**
The transition classes depend on standardized global averages, which may obscure region-specific baselines or development constraints. Percent change in demand per capita can also exaggerate growth for countries starting from low baselines. Additionally, the Top-15 pressure framing prioritizes extremes and may underrepresent moderate but structurally important cases. Finally, the view emphasizes association rather than causality—policy, resource endowment, and market structure are not directly encoded. Certain aesthetci improvements could possibly made as well.

---

## **Individual Summary**

This project helped me better understand how coordinated multi-view dashboards can support complex analytical questions when interaction logic is carefully constrained. Designing View I emphasized the importance of grounding visual analysis in interpretable derived metrics, while View II pushed me to think more abstractly about classification and typologies rather than raw values alone. One of the most valuable lessons was learning how quickly interactions can become misleading if defaults are not thoughtfully designed—features like conditional rendering and opacity-based highlighting significantly improved interpretability.

From a data perspective, the dashboards reinforced that energy transitions are uneven and context-dependent. Some countries manage to expand renewables alongside growing demand, while others face mounting pressure as demand accelerates faster than clean capacity. Importantly, these patterns are not purely technical outcomes but reflections of economic structure, governance, and infrastructure constraints.

If I had more time, I would extend the analysis by introducing region-normalized benchmarks and uncertainty cues, and by incorporating additional explanatory variables such as income level or grid interconnection capacity. Overall, this project strengthened my ability to translate high-level analytical questions into interactive visual systems that balance exploration, clarity, and restraint.
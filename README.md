# ecommerce_AB_Test_SQL_Python

This is a Python project of mine created with the goal of analyzing results of multiple A/B Tests conducted on e-commerce data. We analyzed 4 metrics: `add_payment_info`, `begin_checkout`, `add_shipping_info` and `new_account`, expecting significant improvements. As a result of our A/B tests, only Test 1 showed significant improvements in most of the metrics, while the other tests should be rejected based on the output.

## **AB Test Results - Overall Conclusions**

### **1. Test Performance Summary**

**Test 1**
- **3 out of 4 metrics showed significant positive improvements**
- Best performer across all tests with strong lifts in key conversion funnel metrics:
  - `add_payment_info`: **+12.54%** (p=0.0001), highly statistically significant
  - `begin_checkout`: **+6.66%** (p=0.0029), statistically significant
  - `add_shipping_info`: **+6.56%** (p=0.0092), statistically significant
- Only `new_account` showed a non-significant decrease (-3.35%, p=0.1229)
- **Recommendation:** Test 1 should be rolled out to production

**Test 2**
- **0 out of 4 metrics were statistically significant**
- All metrics showed marginal positive lifts (+1.24% to +3.58%) but none reached significance
- **Recommendation:** Discard this variant, changes had no measurable effect

**Test 3**
- **1 out of 4 metrics significant, but in the wrong direction**
- `begin_checkout` significantly **decreased by -3.35%** (p=0.0120)
- Other metrics showed no significant changes
- **Recommendation:** Do not implement, this variant hurt checkout conversion

**Test 4**
- **2 out of 4 metrics significant, both negative**
- `begin_checkout`: **-2.35%** (p=0.0459), significant decrease
- `new_account`: **-3.36%** (p=0.0175), significant decrease
- **Recommendation:** Do not implement, this variant actively harmed performance

---

### **2. Segment-Level Insights**

**Geographic Performance:**
- **Europe** showed the highest % of significant results (37.5% of tests), suggesting European users may be more sensitive to UI/UX changes
- **Americas and Africa** both showed 18.8% significance rates, changes had moderate impact
- **Asia** at 22.9%, middle performer
- **Unknown** continent showed 50% significance, but this is likely due to small sample sizes and should be interpreted cautiously

**Device Performance:**
- **Desktop** users showed the most significant results (32.3%), indicating desktop experience changes had the strongest measurable impact
- **Mobile** followed at 28.1%, still substantial but slightly less pronounced
- **Tablet** showed the lowest rate at 25%, either smallest sample sizes or tablet users are less affected by changes

---

### **3. Recommendations**

1. **Implement Test 1 immediately**, it's a proven winner with strong statistical backing
2. **Do not implement Tests 2, 3, or 4**, they either had no effect or actively hurt performance
3. **Investigate the account creation issue**, why did multiple tests negatively impact `new_account`? Consider running a dedicated test focused on improving registration UX
4. **Consider regional rollouts**, given Europe's higher sensitivity to changes, consider testing future variants there first before global rollout
5. **Focus on mobile optimization next**, mobile showed slightly lower significance rates, suggesting room for improvement in mobile-specific UX

## Useful links
[Tableau Dashboard](https://public.tableau.com/views/ABTestDashboard_17717866785340/ABTest?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)  
[CSV output (Drive link)](https://drive.google.com/file/d/1ZiYnRU630h9UK75EYdHs9LFTeBO3murX/view?usp=sharing)

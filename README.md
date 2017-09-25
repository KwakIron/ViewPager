# ViewPager
```
public class MainActivity extends AppCompatActivity {
    private TabLayout tab;
    private ViewPager pager;
    private Fragment one,two,three;
    private List<Fragment> datas = new ArrayList<>();


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        initView();
        PagerAdapter adapter = new PagerAdapter(getSupportFragmentManager(),datas);
        pager.setAdapter(adapter);
        pager.addOnPageChangeListener(new TabLayout.TabLayoutOnPageChangeListener(tab));
        tab.addOnTabSelectedListener(new TabLayout.ViewPagerOnTabSelectedListener(pager));
    }
    private void initView(){
        tab = (TabLayout)findViewById(R.id.tabLayout);
        pager = (ViewPager)findViewById(R.id.viewPager);
        tab.addTab(tab.newTab().setText("one"));
        tab.addTab(tab.newTab().setText("two"));
        tab.addTab(tab.newTab().setText("three"));
        one = new OneFragment();
        two = new TwoFragment();
        three = new ThreeFragment();
        datas.add(one);
        datas.add(two);
        datas.add(three);
    }
    class PagerAdapter extends FragmentStatePagerAdapter{
        List<Fragment> datas;
        public PagerAdapter(FragmentManager fm,List<Fragment> datas) {
            super(fm);
            this.datas = datas;
        }

        @Override
        public Fragment getItem(int position) {
            return datas.get(position);
        }

        @Override
        public int getCount() {
            return datas.size();
        }
    }
}

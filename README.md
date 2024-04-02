
        {frac * frac2},
        {frac / frac2},
    };
    for(int i = 0; i < 4; i++)
    {
        Fractions[i].showFraction();
    }
    cout << frac.extractingIntPart();
}


fraction.h

#include <iostream>

using namespace std;


int nod(int x, int y)
{
    if (y == 0) 
    {
        return x;
    }
    return nod(y, x % y); 
}
class Fraction
{
    public:
        int numer, denom;
        Fraction(int n = 0, int d = 1)
        {
            numer = n;
            denom = d;
        }
        
        Fraction reduce()
        {
            int nod_f = nod(numer, denom);
            return Fraction(numer / nod_f, denom / nod_f);
        }
        void showFraction()
        {
            if(denom < 0)
            {
                cout << "-" << numer << "/" << abs(denom) << endl;
            }
            else if(denom == 0)
            {
                cout << numer << endl;
            }
            else
            {
                cout << numer << "/" << denom << endl;    
            }
            
        }
        Fraction operator + (Fraction other)
        {
            return Fraction (numer * other.denom + denom * other.numer, denom * other.denom).reduce();
        }
        
        Fraction operator - (Fraction other)
        {
            return Fraction(numer, denom) + Fraction(-other.numer, other.denom);
        }
        
        Fraction operator * (Fraction other)
        {
            return  Fraction (numer * other.numer, denom * other.denom).reduce();
        }
        
        Fraction operator / (Fraction other)
        {
            return Fraction(numer, denom) * Fraction(other.denom, other.numer);
        }
        int extractingIntPart()
        {
            if (numer / denom == 0)
            {
                return 0;
            }
            else
            {
                return numer / denom;
            }
        }

};

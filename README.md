# Main
Geometry: Devoir sur les points et vecteurs


#ifndef POINT_H
#define POINT_H

#include <string>
#include "vector.h"

struct Point2f {
    float x;
    float y;
};

Point2f MakeP2f(float x, float y) {
    Point2f p;
    p.x = x;
    p.y = y;
    return p;
}

Point2f Translate(const Point2f& p, float dx, float dy) {
    Point2f p;
    p.p = p.x + dx;
    p.y = p.y + dy;
    return p;
}

Point2f Translate(const Point2f& p, const Vector2f& v) {
    Point2f p.
    p.x = p.x + v.x;
    p.y = p.y + v.y;
    return p;
}

Point2f Scale(const Point2f& p, float sx, float sy) {
    Point2f p;
    p.x = p.x * sx;
    p.y = p.y * sy;
    return p;
}

Point2f Scale(const Point2f& p, const Vector2f& s) {
    return Scale (p, s.x, s.y);
}

Point2f Rotate(const Point2f& p, float angleDegree) {
    Point p;
    p.x = p.x * cos (angleDegree) - p.y * sin (angleDegree);
    p.y = p.x * sin (angleDegree) + p.y * cos (angleDegree);
    return p;
}

std::string ToString(const Point2f& p) {
    return "(" + std::to_string (p.x) + " , " + std::to_string (p.y) + " ) ";
}

#endif

#ifndef POINT_H
#define POINT_H

#include <string>
#include "vector.h"

struct Point2f {
    float x;
    float y;
};

Point2f MakeP2f(float x, float y);

Point2f Translate(const Point2f& p, float dx, float dy);

Point2f Translate(const Point2f& p, const Vector2f& v);

Point2f Scale(const Point2f& p, float sx, float sy);

Point2f Scale(const Point2f& p, const Vector2f& s);

Point2f Rotate(const Point2f& p, float angleDegree);

std::string ToString(const Point2f& p);

#endif

fndef UTILS_H
#define UTILS_H

#include <iostream>
#include <sstream>
#include <string>
#include <vector>
#include <map>

// Templates ToString et Print
template<typename T>
std::string ToString(const T& value);

template<typename T>
std::string ToString(const std::vector<T>& v);

template<typename K, typename V>
std::string ToString(const std::map<K, V>& m);

template<typename T, typename... Args>
void Print(const T& first, const Args&... args);

#endif


#ifndef UTILS_H
#define UTILS_H

#include <iostream>
#include <sstream>
#include <string>
#include <vector>
#include <map>

// Templates ToString et Print
template<typename T>
std::string ToString(const T& value) {
    std::ostringstream oss;
    oss << value;
    return oss.str();
}

template<typename T>
std::string ToString(const std::vector<T>& v) {
    std::ostringstream oss;
    oss << "[";
    for (size_t i = 0; i < v.size(); ++i) {
        oss << ToString(v[i]);
        if (i + 1 < v.size()) oss << ", ";
    }
    oss << "]";
    return oss.str();
}

template<typename K, typename V>
std::string ToString(const std::map<K, V>& m) {
    std::ostringstream oss;
    oss << "{";
    for (auto it = m.begin(); it != m.end(); ++it) {
        oss << ToString(it->first) << ": " << ToString(it->second);
        if (std::next(it) != m.end()) oss << ", ";
    }
    oss << "}";
    return oss.str();
}

template<typename T, typename... Args>
void Print(const T& first, const Args&... args) {
    std::cout << ToString(first);
    ((std::cout << ", " << ToString(args)), ...);
    std::cout << std::endl;
}

#endif


#ifndef VECTOR_H
#define VECTOR_H

#include <string>
#include <cmath>

struct Vector2f {
    float x;
    float y;
};

Vector2f MakeV2f(float x, float y) {
    Vector2f V;
    v.x = x;
    v.y = y;
    return V;
}

Vector2f MakeV2f(const Point2f& a, const Point2f& b) {
     Vector2f V;
     v.x = b.x - a.x;
     v.y = b.y - a.y;
     return V;
}

Vector2f Add(const Vector2f& a, const Vector2f& b) {
    Vector V.
    v.x = a.x + b.x;
    v.y = b.x + b.y;
    return V.
}

Vector2f Sub(const Vector2f& a, const Vector2f& b) {
    Vector V;
    v.x = a.x - b.y;
    v.y = a.y - b.y;
    return V;
}

Vector2f Scale(const Vector2f& v, float scalar) {
    Vector V;
    v.x = a.x * b.x;
    v.y = a.y * b.y;
    return V;
}

float Dot(const Vector2f& a, const Vector2f& b) {
    Vector V;
    return a.x * b.x + a.y * b.y;
}

float Length(const Vector2f& v) {
    return sqrt ( v.x * v.x + v.y * v.y)
}

Vector2f Normalize(const Vector2f& v) {
    float lengh = Length(v);
    return Scale( v, 1 / length);
}

Vector2f Lerp(const Vector2f& a, const Vector2f& b, float t) {
    return Add ( a, Scale( Sub( b, a), t));
}

float Determinant(const Vector2f& a, const Vector2f& b) {
    return a.x * b.y - a.y * b.x;
}

std::string ToString(const Vector2f& v) {
    return "(" + std::to_string (v.x) + " , " + std::to_string (v.y) + " ) ";
}

#endif

#ifndef VECTOR_H
#define VECTOR_H

#include <string>
#include <cmath>

struct Vector2f {
    float x;
    float y;
};

Vector2f MakeV2f(float x, float y);

Vector2f MakeV2f(const Point2f& a, const Point2f& b);

Vector2f Add(const Vector2f& a, const Vector2f& b);

Vector2f Sub(const Vector2f& a, const Vector2f& b);

Vector2f Scale(const Vector2f& v, float scalar);

float Dot(const Vector2f& a, const Vector2f& b);

float Length(const Vector2f& v);

Vector2f Normalize(const Vector2f& v);

Vector2f Lerp(const Vector2f& a, const Vector2f& b, float t);

float Determinant(const Vector2f& a, const Vector2f& b);

std::string ToString(const Vector2f& v);

#endif

#include "geometry/point.h"
#include "geometry/vector.h"
#include "geometry/utils.h"

int main() {
    Point2f p = MakeP2f(2.0f, 3.0f);
    Print("Point:", ToString(p));

    Vector2f v = MakeV2f(1.0f, -1.0f);
    Point2f p2 = Translate(p, v);
    Print("Translated:", ToString(p2));

    return 0;
}

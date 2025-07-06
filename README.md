// تطبيق متجر مال ماس - نسخة أولى
// إطار العمل: React Native مع Expo لدعم Android و iOS
// مكتبة التنقل: React Navigation
// اللغة: عربي - إنجليزي

import React from "react";
import { NavigationContainer } from "@react-navigation/native";
import { createNativeStackNavigator } from "@react-navigation/native-stack";
import { Text, View, I18nManager, Image, ScrollView } from "react-native";
import { Button } from "@/components/ui/button";

I18nManager.forceRTL(true); // دعم اللغة العربية من اليمين لليسار

const Stack = createNativeStackNavigator();

function HomeScreen({ navigation }) {
  return (
    <ScrollView className="flex-1 bg-white p-4">
      <Text className="text-2xl font-bold mb-4 text-right">مرحباً بك في مال ماس</Text>
      <Image source={{ uri: 'https://mal-mas.com/logo.png' }} className="w-full h-40 rounded-2xl mb-4" resizeMode="contain" />

      <Button onPress={() => navigation.navigate('Products')} className="mb-2">تصفح المنتجات</Button>
      <Button onPress={() => navigation.navigate('Offers')} className="mb-2">العروض والتخفيضات</Button>
      <Button onPress={() => navigation.navigate('Contact')}>تواصل معنا</Button>
    </ScrollView>
  );
}

function ProductsScreen() {
  // لاحقاً: جلب المنتجات من قاعدة البيانات أو API
  return (
    <ScrollView className="p-4">
      <Text className="text-xl font-semibold text-right mb-2">وصل حديثاً</Text>
      {/* عينة من منتج */}
      <View className="bg-gray-100 rounded-2xl p-4 mb-4">
        <Image source={{ uri: 'https://mal-mas.com/sample.jpg' }} className="w-full h-40 rounded-xl mb-2" resizeMode="cover" />
        <Text className="text-right font-bold">فستان راقي</Text>
        <Text className="text-right text-gray-700">السعر: 11000 (شامل التوصيل)</Text>
      </View>
    </ScrollView>
  );
}

function OffersScreen() {
  return (
    <View className="flex-1 items-center justify-center p-4">
      <Text className="text-lg">تابع العروض الخاصة قريباً!</Text>
    </View>
  );
}

function ContactScreen() {
  return (
    <View className="flex-1 items-center justify-center p-4">
      <Text className="text-lg text-center">للتواصل معنا عبر الواتساب:
      {'\n'}واتساب: 777777777
      {'\n'}أو عبر انستجرام @malmas.official
      </Text>
    </View>
  );
}

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} options={{ title: 'مال ماس' }} />
        <Stack.Screen name="Products" component={ProductsScreen} options={{ title: 'المنتجات' }} />
        <Stack.Screen name="Offers" component={OffersScreen} options={{ title: 'العروض' }} />
        <Stack.Screen name="Contact" component={ContactScreen} options={{ title: 'تواصل معنا' }} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
